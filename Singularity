Bootstrap: docker
FROM: continuumio/miniconda3:latest

%labels
    Maintainer Jeremy Magland
    Version 0.1.0
    InstalledBy Michael Montgomery


%setup

%post
  echo "############## apt-get update & install (misc)"
  
  apt-get update -y && apt-get upgrade -y
  apt-get install apt-utils build-essential \
  	  	  libgtk-3-0 \
		  libxss1 \
		  libgconf-2-4 \
		  libnss3 -y

#  	  	       clang libdbus-1-dev libgtk-3-dev \
#		       libnotify-dev libgnome-keyring-dev libgconf2-dev \
#                       libasound2-dev libcap-dev libcups2-dev libxtst-dev \
#                       libxss1 libnss3-dev gcc-multilib g++-multilib curl \
#                       gperf bison python-dbusmock -y

  echo "############## install nodejs #############"
  curl -sL https://deb.nodesource.com/setup_11.x | bash -
  apt-get install -y nodejs

  echo "############## install electronjs #########"
  npm i -D electron@latest

  echo "################################## Activating conda environment"
  . /opt/conda/etc/profile.d/conda.sh
  conda create -n mountainlab
  conda activate mountainlab

  echo "################################## Installing Python"
  conda install python=3.6

  echo "################################## Installing MountainLab"
  conda install -c flatiron -c conda-forge \
  		   	    mountainlab \
			    mountainlab_pytools \
			    ml_ephys \
			    ephys-viz \
			    ml_ms3 \
			    ml_ms4alg \
			    ml_pyms \
			    qt-mountainview

#  echo "################################# modify fontconfig to fix bug"
#  conda install -c conda-forge fontconfig==2.12.6
  
  echo "################################## Testing installation"
  ml-list-processors

%environment
  . /opt/conda/etc/profile.d/conda.sh
  conda activate mountainlab
