Outline

* SFTP endpoint
    * auth
    * drop file in "incoming-files" bucket
    * add message to Pub/Sub
* Injest worker
    * Read from Pub/Sub
    * Import from "incoming-files" bucket
    * Archive on success, requeue task on failure
    * ? follow up job for analysis
* Website
    * Should display the top 5 "easiest" positions to be elected to by browser detected location
        * easiest meaning uncontested and lowest vote count, petition signature count, filing fee, residency length, minimum age, time commitment (in that order)
        * should not feature repeats like "JUDGE OF ELECTION-29-17" and "JUDGE OF ELECTION-58-44"
    * Allow for querying/searching based on numeric fields, party, and location

Import fields
Name (string) - 
Desciption (string) - 
Uncontested (boolean) - True if one or zero



Probably use a blacklist to exclude certain "offices" like bond questions, No Vote, Charter Change, et cetera.
Use the multiple occurances of an office to get the number of candidates (and something to handle the write in line).


sudo docker build -t elect-me-web .
sudo docker run -t -p 8085:80 elect-me-web


