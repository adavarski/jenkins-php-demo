node {

  stage "Checkout Git repo"
    checkout scm
  stage "Build RPM"
    sh "[ -d ./rpm ] || mkdir ./rpm"
    sh "docker run -v \$(pwd)/src:/data/demo-app -v \$(pwd)/rpm:/data/rpm --rm tenzer/fpm fpm -s dir -t rpm -n demo-app -v \$(git rev-parse --short HEAD) --description \"Demo PHP app\" --directories /var/www/demo-app --package /data/rpm/demo-app-\$(git rev-parse --short HEAD).rpm /data/demo-app=/var/www/"
  stage "Update YUM repo"
    sh "[ -d ~/repo/rpm/demo-app/ ] || mkdir -p ~/repo/rpm/demo-app/"
    sh "mv ./rpm/*.rpm ~/repo/rpm/demo-app/"
  }
