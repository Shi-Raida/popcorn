Bootstrap: docker
From: ubuntu:xenial

%setup
REPO_ROOT=`dirname $SINGULARITY_BUILDDEF`
cp -r $REPO_ROOT/ $SINGULARITY_ROOTFS/planner

%post
apt-get update
apt-get -y install g++ make flex bison cmake doxygen coinor-clp coinor-libcbc-dev coinor-libclp-dev coinor-libcoinutils-dev coinor-libosi-dev coinor-libcgl-dev libbz2-dev libgsl-dev libz-dev

%runscript
DOMAINFILE=$1
PROBLEMFILE=$2
PLANFILE=$3
/planner/planner/popf/popf3-clp $DOMAINFILE $PROBLEMFILE > $PLANFILE

%test
/planner/planner/popf/popf3-clp

%labels
Name        popcorn-base
Description 2018 version of popcorn base
Authors     Emre Savas and Maria Fox and Derek Long
SupportsDerivedPredicates yes
SupportsQuantifiedPreconditions yes
SupportsQuantifiedEffects yes
