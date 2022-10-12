# HOW-TO-GET-IP-IN-DJANGO
easily get ip in djnago simple method


## MODELS 

```
class GenderCategory(models.Model):
    gender              =   models.CharField(max_length=255,blank=True,null=True) 
    is_active           =   models.BooleanField(default=True)
    created_date        =   models.DateTimeField(auto_now_add=True)
    created_id          =   models.ForeignKey(User,on_delete=models.CASCADE,related_name='gender_created_user',null=True, blank=True)
    created_ip          =   models.GenericIPAddressField(null=True, blank=True)
    modified_date       =   models.DateTimeField(auto_now=True)
    modified_id         =   models.ForeignKey(User,on_delete=models.CASCADE,related_name='gender_modifide_user',null=True, blank=True)
    modified_ip         =   models.GenericIPAddressField(null=True, blank=True)
    record_status       =   models.CharField(max_length=255,default='created',null=True, blank=True)
    
    def __str__(self):
        return self.gender
 ```
 
 `` created_ip   =   models.GenericIPAddressField(null=True, blank=True)``
 
 ## views
 
 ```
 def get_client_ip(request):
    x_forwarded_for = request.META.get('HTTP_X_FORWARDED_FOR')
    if x_forwarded_for:
        ip = x_forwarded_for.split(',')[0]
    else:
        ip = request.META.get('REMOTE_ADDR')
    return ip
    ```
