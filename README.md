# alamose-workshop-sandbox

# First import necessary libraries



from http import client

from itertools import count

from venv import create

import hvac

import random



# This function will create the connection with the vault.

def makeConnection():

   hvc_client = hvac.Client(url='asfdasdf', token='asdfasdf' )

   return hvc_client





# This fuction will save or store secreate data to the vault

def storeSecret(client, secr1, cnt):

   secret_path = 'SECRET_PATH_' + str(cnt)

   create_response = client.secrets.kv.v2.create_or_update_secret(path='secret-path-1', secret=dict(password='Hashi123'))





# This function will get or retrieve the data for secrtet from the vault.

def retrieveSecret(client_, cnt_):

   secret_path = 'SECRET_PATH_' + str(cnt_)

   read_response      = client_.secrets.kv.read_secret_version(path='secret-path-1')

   secret_from_vault  = read_response['data']['data']['password']

   print(secret_from_vault)





# Main function to start the program

if __name__ == '__main__':

   clientObject = makeConnection()

   secretToStore = 'A_VERY_SPECIAL_SECRET'

   counter = 0



   print('The secret we want to store ', secretToStore)

   print('='*50)

   storeSecret(clientObject, secretToStore, counter)

   print('=' * 50)



   retrieveSecret(clientObject, counter)

   print('=' * 50)
