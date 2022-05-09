HERE := ${CURDIR}

CONTAINER := ionic

build:
	docker build -t ${CONTAINER} .

run:
	docker run  -p 0.0.0.0:4200:4200 -v ${HERE}/../Workspace:/workspace -it ${CONTAINER}


new:
	echo "ng new app --strict --style scss --package-manager yarn  --skip-git --routing"
	echo "cd add"
	echo "yarn add @angular/material @angular/cdk"

apps:
	echo "git clone https://github.com/angular/material-start"	