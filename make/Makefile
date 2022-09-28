# usage:
# make all           # Will upload all files to s3 AWS
# make upload_win_fs #  Will upload only the file you name
# make clean         # Will remove the files from the current directory structure
                     # no change is made on S3
# variables
WIN_FS := WIN_FS_FILENAME
LNX_FS := LNX_FS_FILENAME
LNX_ORA := LNX_ORA_FILENAME
WIN_MSSQL := WIN_MSSQL_FILENAME

.DEFAULT_GOAL := list

.PHONY: list
list:
        @echo "* * * Showing list of targets in makefile * * *"
        @LC_ALL=C $(MAKE) -pRrq -f $(lastword $(MAKEFILE_LIST)) \
        : 2>/dev/null | awk -v RS= -F: '/(^|\n)# Files(\n|$$)/,/(^|\n) \
        # Finished Make data base/ {if ($$1 !~ "^[#.]") {print $$1}}' \
        # | sort | egrep -v -e '^[^[:alnum:]]' -e '^$@$$'

all: zip_all upload_win_fs upload_lnx_fs upload_lnx_oracle upload_win_mssql

zip_all:
        @echo "zip it"

upload_all: upload_win_fs upload_lnx_fs upload_lnx_oracle upload_win_mssql

upload_win_fs:
        @echo ${WIN_FS}

upload_lnx_fs:
        @echo ${LNX_FS}

upload_lnx_oracle:
        @echo ${LNX_ORA}

upload_win_mssql:
        @echo ${WIN_MSSQL}

help: list
        @echo "RTFM"

clean:
        @echo "Let's clean it up"
