# @(#) $Tau: tdk/docker/tdk/Makefile.am $

## ------------------------------------------------------------------------- ##
##                          T A U    P R O J E C T                           ##
## ------------------------------------------------------------------------- ##
##                                                                           ##
##  Licensed under the Apache License, Version 2.0 (the "License");          ##
##  you may not use this file except in compliance with the License.         ##
##                                                                           ##
##  You may obtain a copy of the License at:                                 ##
##                                                                           ##
##      http://www.apache.org/licenses/LICENSE-2.0                           ##
##                                                                           ##
##  Unless required by applicable law or agreed to in writing, software      ##
##  distributed under the License is distributed on an "AS-IS" BASIS,        ##
##  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. ##
##  See the License for the specific language governing permissions and      ##
##  limitations under the License.                                           ##
##                                                                           ##
## ------------------------------------------------------------------------- ##

IMAGE = tdk
IMAGENAME = $(ORG)/$(IMAGE)

if WITH_DOCKER

all-local: container
	
container:
	$(DOCKER) build -t $(IMAGENAME) $(srcdir)
	$(DOCKER) tag $(IMAGENAME) $(IMAGENAME):$(RELEASE)

push: container
	$(DOCKER) push $(IMAGENAME)
	$(DOCKER) push $(IMAGENAME):$(RELEASE)
	
run: shell

shell: container
	@printf "\n" >&2
	@printf "Launching a shell within %s\n\n" '$(IMAGENAME)' >&2
	@printf "NOTE: Changes made within the container will not be saved.\n\n" >&2
	@printf "Type 'exit' to shut down the container." >&2
	@printf "\n" >&2
	@$(DOCKER) run -it $(IMAGENAME)

else

container push run shell:
	@printf "Warning: Docker is not available for this build; skipping\n" >&2

endif
