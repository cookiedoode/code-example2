The scenario:
- There is a need to delete existing url alias table and regenerate the url aliases using the bulk generator. 

The problem:
- The client has thousands of nodes that utilize custom url alias. When the table is removed, the custom url alias is removed as well, utlimately stripping previous url aliases from nodes that utilize custom url alias. This first function should be run before the url alias table has been cleared.

The solution:
- The first function in the module will identify which node has the auto alias checkbox unchecked and grab the string from the custom url alias field along with the nid and create a file called response.json.
- The second function in the module will use the response.json file and reinsert the custom url aliases according to their nid. This second function should be run after the url alias table has been cleared.

Instruction:
- Install and activate the module
- Run the functions using drush in the environment:
    - drush php-eval "generate_url_alias_list()"
    - drush php-eval "reinsert_custom_url_alias()"  