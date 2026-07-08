thm - linux fundamentals part 1:
super basic but essential. most web servers, target boxes, and tools run on linux, so you gotta know this stuff cold before doing any actual hacking/ctfs.

paths & moving around
absolute paths: starts from the very root / (e.g., /home/kali/Desktop).
relative paths: starts from wherever you are standing right now (e.g., Documents/).

pwd - where am i? run this before deleting stuff so you don't break the system.

cd - change directory.
cd .. - go back one folder.
cd ~ - go straight home.
cd - - jump back to the last folder you were just in.

checking stuff out (ls)
ls - just lists files. pretty boring by itself.
ls -l - the detailed view. shows who owns the file and permissions (clutch for privilege escalation later).
ls -a - shows hidden files (the ones starting with a .). things like .bash_history or .ssh live here.
ls -lah - the holy grail. combines everything: detailed, shows hidden files, and makes sizes human-readable (e.g., 4K instead of 4096).

files & folders
mkdir - make a folder.
mkdir -p path/to/folder - forces it to create the parent folders if they don't exist yet so it doesn't error out.

touch - creates an empty file. cool for spinning up a quick note or wordlist.

cat - dumps file contents onto your screen.
cat -n - adds line numbers. great for code or huge configs.

rm - delete a file.
rm -r - delete a folder.
rm -rf - the nuclear option. forces deletion of a folder and everything inside it without asking questions. use carefully.

cp - copy. (needs -r if you're copying a whole folder).

mv - move OR rename a file.

text manipulation (echo & grep)
echo - prints text to screen. echo $USER checks variables.
echo -n "text" - drops the invisible newline at the end. you'll need this when making raw strings to generate clean md5 hashes.

grep - search engine for text.
grep "flag" notes.txt - finds the word flag.
grep -i - ignores case (matches Flag, FLAG, flag).
grep -r "password" . - searches every single file in the current folder and subfolders.
grep -v "success" - shows everything except lines containing "success". great for filtering noise out of logs.

operators (chaining stuff together)
> - pipe output into a file and overwrite everything in it.

echo "admin" > user.txt

>> - pipe output into a file but append it to the bottom.

echo "guest" >> user.txt

| - the pipe. takes the output of command A and feeds it into command B.

cat /etc/passwd | grep "kali"

; - run multiple commands in a row, even if one fails.

mkdir loot; cd loot; touch flag.txt

