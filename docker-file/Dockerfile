FROM ubuntu:21.04

#we need to add a timezone variable cause it will hang for newer versions
ENV TZ=Europe/Belgrade
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV LD_LIBRARY_PATH=/urs/lib:/usr/local/lib

RUN apt-get update -y && \
		apt-get install -y libc6 libc6-dev g++ cmake git build-essential libgl1-mesa-dev libsoil-dev libglm-dev libassimp-dev libglew-dev libglfw3-dev libxinerama-dev libxcursor-dev libxi-dev mesa-common-dev mesa-utils libxxf86vm-dev libfreetype6-dev freeglut3-dev libspdlog-dev	 	

COPY . /usr/src/rg-project

WORKDIR /usr/src/rg-project

RUN git clone https://github.com/pearpanda/computer-graphics-project && \
	  echo "Cloning finished. Listing project: " && \
		echo $LD_LIBRARY_PATH && \
		
		echo "Creating a soft link for our libm.so library: " && \
		ln -s /usr/lib/x86_64-linux-gnu/libm.so /usr/lib/libm.so && \
		echo "Soft link created successfully." && \
		ls -la /usr/lib/libm.so && \
		echo "Changing to project path: " && \
		cd computer-graphics-project && \
		echo "Creating build directory for cmake: " && \
		mkdir build && \
		echo "Navigating to build: " && \
		cd build && \
		echo "Building the program. Please wait" && \
		cmake .. -G "Unix Makefiles" && \
		echo "Listing make options. You will need to change the Dockerfile. " && \
		make help && \
		echo "Building executables." && \
		make rg 



