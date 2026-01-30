# Local LLM-powered RAG-driven file inspection service
I have changed multiple jobs, switched many desktop computers, laptops, with different operating systems. I used different directory structures to store my files during different periods of my life, both personal and not. I have excercised slacking discipline in terms of my file and directory naming, sometimes saving a *temporary* file version with a name like `Resume (3) - copy copy_new_backup.doc` and never came back to clean it up and rename it properly.

All this stuff has been accumulating on my hard disk first, migrating from computer to computer, then moved to a cloud file storage **as is**, then was partially copied to another, and, perhaps, another... For historical reasons I store my e-book collection in Dropbox, documents on my computer is syncronized with Google Drive (also partially with OneDrive, but unintentionally), video recordings of my music concerts are stored in Yandex Disk...

Those are the things *I think* I remember. There is a ton of stuff that is stored on everywhich service, that I don't have a clue about.

I decided to write a service, which would index the information on my disk (local or otherwise) and answer simple question of `What is inside this directory?`
## Use cases
### What's inside this directory?
A user selects a directory in their OS and asks the service to tell them, what files are inside. The service categorises the files in the directory and returns a summary of the categories to the user.

## Architecture
I will use a local LLM (small one to fit into my 4Gb GF3050 mobile GPU) to index the documents, store the embeddings in a local vector DB. Upon a user query the service will check if all files in the directory have been indexed, perform cluster analyzis on the embedding vectors, corresponding to the files in the directory, for every cluster found a summary will be generated to describe the nature of the documents.