---

Tags : #tools #gzip #tar #compress
Back Links :
Date : {{17-07-2022}} 00:17

---

# gzip
## compress command:
`gzip {file_to_compress}
ex:
`gzip file.txt
will result a file with extention .gz
`file.gz`

see compression ratio:
`gzip -l file.txt.gz

## decompress
`gzip -d  file.txt.gz

## compress directory:
Use archiver like *tar*, and add *z* flag
`tar -czvf {output_file}.gz {directory_to_compress}
ex:
`tar -czvf compressed.tar.gz thefolder
