oauth2-sina-and-qq
==================

sina and qq oauth2 API client

Usage:

from oauth.oauth2 import APIClient

    sina = APIClient( app_key='2198251111', 
                        app_secret='xxxxx', 
                        redirect_uri='http://url', 
                        domain='api.weibo.com',
                        oauth_uri='oauth2',
                        format='json',
                        version='2',
                        type='sina')


    qq = APIClient(app_key='100497365', 
                   app_secret='xxxx'
                   redirect_uri='http://url',
                   domain='graph.qq.com',
                   oauth_uri='oauth2.0',
                   type='qq') 
     
def login_qq(request):                   
    url = qq.get_authorize_url(state=state)  
    return HttpResponseRedirect(url)
    
def auth_qq(request):
    token = qq.request_access_token(code, token_uri='token', method='GET')   
    id = qq.request_openID()
    qq.set_request_params(oauth_consumer_key=id.client_id,
                              openid = id.openid,
                              access_token = token.access_token)
    userinfo = qq.user__get_user_info(format='json')
