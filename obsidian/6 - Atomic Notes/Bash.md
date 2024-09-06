>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

How to redirect output to a file and stdout

ls |& tee files.txt

If ‘|&’ is used, command1’s standard error, in addition to its standard output, is connected to command2’s standard input through the pipe; it is shorthand for 2>&1 |. This implicit redirection of the standard error to the standard output is performed after any redirections specified by the command.

if you only care about stdout:
ls -a | tee output.file

If you want to include stderr, do:
program [arguments...] 2>&1 | tee outfile

2>&1 redirects channel 2 (stderr/standard error) into channel 1 (stdout/standard output), such that both is written as stdout. It is also directed to the given output file as of the tee command.

Furthermore, if you want to append to the log file, use tee -a as:
program [arguments...] 2>&1 | tee -a outfile

Ref:
https://stackoverflow.com/questions/418896/how-to-redirect-output-to-a-file-and-stdout


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

libreoffice - openoffice alternative to convert doc to pdf

/opt/libreoffice7.5/program/soffice --headless --convert-to pdf --outdir . FE_sanction_letter_format_core.odt >/dev/null

Multiple instances of soffice.bin at the same time

soffice.exe --headless -env:UserInstallation=file:///c:/temp/Userprofile --convert-to pdf --outdir "C:/temp/PDFs" "C:/temp/input/test.docx"

time soffice --headless -env:UserInstallation=file:///tmp/gjgjgjgjgjg --convert-to pdf --outdir . Hindi2.docx

soffice.exe --headless -env:UserInstallation=file:///c:/temp/Userprofile --convert-to pdf --outdir "C:/temp/PDFs" "C:/temp/input/test.docx"  && rm -r c:/temp/Userprofile

Ref:
https://ask.libreoffice.org/t/multiple-instances-of-soffice-bin-at-the-same-time/95860

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Clean archival log:

. .bash_profile
rman target /
delete archivelog all;
YES
commit;
exit

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

untar-multiple-tar-files

cat *.tar.* | tar -xvf -
cat *.tar.gz.* | tar xvfz -

https://stackoverflow.com/questions/38199571/untar-multiple-tar-gz-aa-tar-gz-ab-pattern-files

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

OCI Image creation using docker

cat >Dockerfile

FROM k8s-registry.nucleussoftware.com/busybox:1.36.1
CMD [ "echo", "OCI-CHECK" ]

Working:

cat >buildkitd.toml
debug = true
insecure-entitlements = [ "network.host", "security.insecure" ]

[registry."k8s-registry.nucleussoftware.com"]
  insecure = true

docker login k8s-registry.nucleussoftware.com
docker buildx create --use --driver docker-container --name oci-builder --config ./buildkitd.toml
docker buildx inspect --bootstrap
docker buildx build --no-cache -t sso:oci .
docker buildx build --no-cache -t k8s-registry.nucleussoftware.com/sso:oci --push .
docker buildx build --no-cache -o type=oci,dest=sso-oci.tar -t k8s-registry.nucleussoftware.com/sso:oci .

Covert Docker to OCI:
apt install skopeo
skopeo login k8s-registry.nucleussoftware.com
skopeo copy -f oci docker://k8s-registry.nucleussoftware.com/sso:jacoco docker://k8s-registry.nucleussoftware.com/sso:oci

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Merge dir like windows:

cd /data01/Software/ollama/qwen2-72b-instruct-q5_K_M
find -type d -exec mkdir -vp ../models/{} \; -or -exec mv -nv {} ../models/{} \;

https://unix.stackexchange.com/questions/127712/merging-folders-with-mv

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>