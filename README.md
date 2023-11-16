# raftlib

Step 1: Update the ubuntu system packages

sudo apt  update && sudo apt -y upgrade && sudo apt -y dít-upgrade && sudo apt -y autoremove && sudo apt autoclean

sudo apt-get -y install build-essential gcc make perl dkms

Step 2: Install required tools and packages

sudo apt-get install build-essential cmake git g++  mpich pkg-config libboost-all-dev




# opencv
sudo apt update
sudo apt install libopencv-dev python3-opencv
python3 -c "import cv2; print(cv2.__version__)"
