✅ Option 1: Transfer Files Using scp (Recommended)
You can copy files from your laptop (Windows) to the AWS instance before SSHing.

Example Command (Run on your local machine, NOT inside SSH)
bash
```
scp -i "your-aws-key.pem" C:\path\to\your\file.txt ubuntu@<EC2-Public-IP>:/home/ubuntu/
🔹 Replace:
```
your-aws-key.pem: Your private key file
C:\path\to\your\file.txt: Your file path
<EC2-Public-IP>: Your instance’s public IP
/home/ubuntu/: Target directory on the instance

✅ Option 3: Use rsync (Advanced)
If you need to sync folders between your C drive and AWS:

bash
```
rsync -avz -e "ssh -i your-aws-key.pem" C:/path/to/your/folder ubuntu@<EC2-Public-IP>:/home/ubuntu/
```
