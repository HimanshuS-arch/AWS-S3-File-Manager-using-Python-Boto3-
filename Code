import boto3
from botocore.exceptions import NoCredentialsError

s3 = boto3.client('s3')

BUCKET_NAME = "your-bucket-name"


def upload_file(file_name):
    try:
        s3.upload_file(file_name, BUCKET_NAME, file_name)
        print("File uploaded successfully!")
    except FileNotFoundError:
        print("File not found")
    except NoCredentialsError:
        print("AWS credentials not available")


def download_file(file_name):
    try:
        s3.download_file(BUCKET_NAME, file_name, "downloaded_" + file_name)
        print("File downloaded successfully!")
    except Exception as e:
        print(e)


def list_files():
    response = s3.list_objects_v2(Bucket=BUCKET_NAME)

    if "Contents" in response:
        print("Files in bucket:")
        for file in response["Contents"]:
            print(file["Key"])
    else:
        print("Bucket is empty")


while True:
    print("\nAWS S3 File Manager")
    print("1. Upload File")
    print("2. Download File")
    print("3. List Files")
    print("4. Exit")

    choice = input("Enter choice: ")

    if choice == "1":
        name = input("Enter file name: ")
        upload_file(name)

    elif choice == "2":
        name = input("Enter file name: ")
        download_file(name)

    elif choice == "3":
        list_files()

    elif choice == "4":
        break

    else:
        print("Invalid choice")
