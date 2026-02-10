`datalake init PATH -c CLIENT -y YEAR -p PROJECT_ID` - Initialize new data lake project with folder structure.
`datalake sync` - Bidirectional sync between local and Azure ADLS Gen2.
`datalake status` - Show sync status (like git status).
`datalake diff [PATH]` - Show detailed changes between local and remote.
`datalake refs add SHARED_PATH` - Add shared data reference to manifest.
`datalake shared fetch [NAME]` - Download shared data to local cache.
`datalake shared download PATH` - Download dataset without requiring project.
`datalake shared upload LOCAL_PATH -t TYPE -p PROVIDER` - Upload local data to shared folder.
`datalake convert file INPUT_PATH --format FORMAT` - Convert file to another format.
`datalake config set KEY VALUE` - Set configuration value.

# Details
## Project Initialization
`datalake init PATH -c CLIENT -y YEAR -p PROJECT_ID` - Create new data lake project with structure.
`datalake init -u https://...` - Initialize from Azure URL (auto-extracts client, year, project-id).
`datalake init -b` - Browse and select from existing Azure projects interactively.
`datalake init --no-ignore` - Skip creating default .datalakeignore file.

## Sync Operations
`datalake sync` - Full bidirectional sync with auto-fetch of shared data.
`datalake sync --push` - Push local changes to Azure only.
`datalake sync --pull` - Pull remote changes from Azure only.
`datalake sync --dry-run` - Preview changes without making them.
`datalake sync --force` - Force sync even if conflicts exist.
`datalake sync --delete` - Delete orphaned files (removed from source).
`datalake sync --resume` - Resume interrupted sync without prompting.
`datalake sync --no-resume` - Start fresh sync, ignore interrupted sync.

## Status & Diff
`datalake status` - Show current branch, local changes, shared refs, ignore info.
`datalake status -r` - Check remote status as well.
`datalake status -s` - Show detailed sync state statistics.
`datalake diff [PATH]` - Show detailed changes with file sizes and times.
`datalake diff processed/` - Filter diff to specific folder.
`datalake log` - Show sync history.
`datalake log -n 5` - Show last 5 sync entries.

## Browsing
`datalake browse` - Browse Azure storage root.
`datalake browse PATH` - Browse specific Azure path.
`datalake browse --local` - Browse local cache instead of Azure.
`datalake browse --local PATH` - Browse cache path.
`datalake browse -d 3` - Show 3 levels deep (default: 2).

## Shared Data References
`datalake refs add SHARED_PATH` - Add shared data reference (copy-by-reference).
`datalake refs add SHARED_PATH -n NAME` - Add with custom name.
`datalake refs add SHARED_PATH --description "desc"` - Add with description.
`datalake refs add SHARED_PATH --link-to data/external/roads` - Add with custom link path.
`datalake refs remove NAME` - Remove a reference.
`datalake refs list` - List all shared data references.
`datalake refs validate` - Validate all references exist in Azure.

## Shared Data Management
`datalake shared fetch NAME` - Fetch specific dataset to local cache.
`datalake shared fetch --all` - Fetch all manifest references (skip cached).
`datalake shared fetch --all --force` - Redownload all datasets.
`datalake shared download PATH` - Download dataset without project (relative to shared/inputs/).
`datalake shared download PATH -q` - Download quietly, only print cache path.
`datalake shared list` - List available shared datasets in Azure.
`datalake shared link` - Link all cached shared data references to project.
`datalake shared delete PATH` - Delete shared dataset from Azure.
`datalake shared delete PATH --yes` - Skip confirmation prompt.
`datalake cache info` - Show cache size and contents.
`datalake cache clear [PATH]` - Clear cached shared data (specify path or --all).

## Shared Data Upload
`datalake shared upload LOCAL_PATH -t TYPE -p PROVIDER` - Upload data to shared folder.
`datalake shared upload LOCAL_PATH -t tabular -p census` - Upload tabular data (census provider).
`datalake shared upload LOCAL_PATH -t gis -p txdot` - Upload GIS data (TxDOT provider).
`datalake shared upload LOCAL_PATH -t gis -p usgs --as-folder` - Upload .gdb preserving structure.
`datalake shared upload LOCAL_PATH --dataset NAME -y YYYY` - Specify dataset name and year.
`datalake shared upload LOCAL_PATH -m MM` - Specify month (MM).
`datalake shared upload LOCAL_PATH --source-url https://...` - Set data source URL.
`datalake shared upload LOCAL_PATH --description "desc"` - Add description.
`datalake shared upload LOCAL_PATH --license "CC-BY"` - Set license.
`datalake shared upload LOCAL_PATH --spatial-coverage Texas` - Set spatial coverage.
`datalake shared upload LOCAL_PATH --temporal-coverage "2020-2024"` - Set temporal coverage.
`datalake shared upload LOCAL_PATH --convert` - Convert files to Parquet before upload.
`datalake shared upload LOCAL_PATH -c snappy` - Set compression (snappy|gzip|zstd|lz4).
`datalake shared upload LOCAL_PATH --yes` - Skip confirmation prompt.

## Format Conversion
`datalake convert file INPUT_PATH` - Convert file to Parquet (default).
`datalake convert file INPUT_PATH --format json` - Convert to JSON.
`datalake convert file INPUT_PATH --format csv` - Convert to CSV.
`datalake convert file INPUT_PATH --format geojson` - Convert to GeoJSON.
`datalake convert file INPUT_PATH -o OUTPUT_PATH` - Specify output path.
`datalake convert file INPUT_PATH -l LAYER` - Specify layer/sheet/table.
`datalake convert file INPUT_PATH -c snappy` - Set compression algorithm.
`datalake convert file INPUT_PATH --list-layers` - List available layers.
`datalake convert dir INPUT_DIR` - Convert all files in directory to Parquet.
`datalake convert dir INPUT_DIR --format csv` - Convert all to CSV.
`datalake convert dir INPUT_DIR -o OUTPUT_DIR` - Specify output directory.
`datalake convert dir INPUT_DIR -p "*.csv" -r` - Convert matching files recursively.
`datalake convert dir INPUT_DIR --dry-run` - Preview without converting.
`datalake convert formats` - List all supported conversion formats.
`datalake convert formats --category spatial` - List spatial formats only.
`datalake convert info INPUT_PATH` - Show schema and metadata for file.
`datalake convert info INPUT_PATH -l LAYER` - Show layer info.

## Metadata Management
`datalake metadata validate` - Validate metadata for all datasets.
`datalake metadata validate PATH` - Validate specific folder.
`datalake metadata generate PATH` - Generate metadata.json template.
`datalake metadata generate PATH --force` - Overwrite existing metadata.
`datalake metadata show PATH` - Display metadata for dataset.

## Remote Management
`datalake remote add NAME https://account.dfs.core.windows.net/container/path` - Add Azure remote.
`datalake remote list` - List configured remotes.
`datalake remote remove NAME` - Remove a remote.

## Configuration Management
`datalake config list` - List all configuration settings.
`datalake config list --global` - Show global config only.
`datalake config list --local` - Show local project config only.
`datalake config get KEY` - Get specific config value.
`datalake config set KEY VALUE` - Set config value (local).
`datalake config set KEY VALUE --global` - Set global config (all projects).
`datalake config types list` - List configured shared data types.
`datalake config types add NAME --extensions ".csv,.parquet"` - Add new data type.
`datalake config types add NAME --description "desc"` - Add type with description.
`datalake config types remove NAME` - Remove data type.

## Authentication
`datalake auth set-key` - Store storage account key in OS credential manager.
`datalake auth set-key -a ACCOUNT_NAME` - Set key for specific account.
`datalake auth delete-key` - Delete stored account key.
`datalake auth delete-key -a ACCOUNT_NAME` - Delete specific account key.
`datalake auth show` - Show current authentication configuration.
`datalake auth test` - Test if authentication is working.

## Ignore Patterns
`datalake ignore show` - Show active ignore patterns and sources.
`datalake ignore test PATH` - Test if path would be ignored during sync.
`datalake ignore create` - Create default .datalakeignore file.
`datalake ignore create --location datalake` - Create .datalake/ignore.
`datalake ignore create --force` - Overwrite existing file.
`datalake ignore add "*.csv"` - Add pattern to .datalakeignore.
`datalake ignore add "temp_data/"` - Ignore directory.
`datalake ignore add "!important.csv"` - Negation pattern (don't ignore).
`datalake ignore remove "*.csv"` - Remove pattern from .datalakeignore.

## Windows Context Menu
`datalake context-menu register` - Add 'Datalake Sync GUI' to right-click menu.
`datalake context-menu unregister` - Remove from context menu.
`datalake context-menu status` - Check if registered.

## Configuration Files
- Global: `~/.config/datalake-sync/config.json` (or Windows Appdata)
- Project: `.datalake/config.json`
- Metadata: `metadata.json` (project root)
- Manifest: `.datalake/manifest.json` (shared data refs)
- Ignore: `.datalakeignore` or `.datalake/ignore`
