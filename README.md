# docker-rails
Simplified ways to host rails applications in docker

## Concept

This repository will contain new docker images for hosting rails applications. In my concept I have 3 distinct configurations for hosting rails applications. Strongly inspired by:
 * https://github.com/ComboStrikeHQ/docker-rails (used as is, building application with Dockerfile)
 * https://github.com/phusion/passenger-docker (can be used with capistrano)
 * https://github.com/ipepe/pnpr (used with capistrano, builtin postgres)

## Requirements
 * All these images should have ability to:
    * stop web server but not container. This is needed for maintenance work or database migrations or backups.
    * generate SECRET_KEY_BASE automatically when it's not present
    * use "old style" volume images where permissions might not be properly done
    * ensure that logs don't kill server space
    * no root access in production, sudo and higher logging levels (friendly errors) in staging or else
    * use rbenv and nodenv for full flexibility in terms of used ruby and node version
    * base it on newest Ubuntu
 * I need docker container for applications that are deplyoed with Capistrano
   * Flexible in terms of background jobs and other worker scripts that might be created on start 
 * I need docker container for simple one time rails application hosting for clients who in future might not have Ruby experienced Admin, it should be as simple as "git pull && docker-compose up --build"
    * Ability to pass ENV variables from docker-compose file
    * Use foreman?
    * Can be used in development for Frontend developers or Junior Ruby programmers

Other requirements, not yet categorized:
 * image does not contain any ruby or node versions, You need to install ruby version when building docker image

