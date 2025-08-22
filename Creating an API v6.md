# Go to Settings > web INTERFACE /APi > Expert mode (top right corner)
<img width="1130" height="666" alt="image" src="https://github.com/user-attachments/assets/46d2e828-bdd5-4fe4-8b00-704da06d579f" />
- Configure password: the password will be marked on the blur area
<img width="541" height="466" alt="image" src="https://github.com/user-attachments/assets/387b4f0c-821b-44d3-8b53-aba7746b30a6" />
- Enable password
<img width="601" height="413" alt="image" src="https://github.com/user-attachments/assets/158d6dd5-5bc8-4a65-8f93-42cbcb314a7b" />
- then enable 2FA
<img width="483" height="283" alt="image" src="https://github.com/user-attachments/assets/26c0dec8-ad08-4c9c-99e5-1cccc0c4d880" />


a googd way to test after wards is:
* sign out > sign in with your new api key
or
* via post call
```
curl -k -X POST "https://10.10.10.2/api/auth" --data '{"password":"cVKlQwSMthwOsjeOss3+sfuOTjRQ7uaQayjdRskr9...}'
```
<img width="1095" height="53" alt="image" src="https://github.com/user-attachments/assets/763bd6ca-6919-4b12-866a-7b41552b8f02" />
