# fastdfs���񼯺�
fastdfs�ķ��񼯺ϣ�����tracker��storage���񣬼��ɰ����Ƶ�yum.repo,ʹ��װ�ٶȸ��ӿ��٣�

# ʹ�ü��
��ǰdocker��docker for windows ������������
- ��������̨fastdfs-tracker������ip:172.17.0.2,ip:172.17.0.3����̨tracker��
- ��������̨fastdfs-storage-dht����(����ip:172.17.0.4��ip:172.17.0.5)��storage������fastdhtʵ���ļ����ع��ܡ�
- �����ϴ�

# ��������
```java
# 172.17.0.2
docker run -dit -p 181:80 -p 22122:22122 --name tracker1 imlzw/fastdfs-tracker
# 172.17.0.3
docker run -dit -p 182:80 -p 22123:22122 --name tracker2 imlzw/fastdfs-tracker
# 172.17.0.4
docker run -dit -p 281:80 -p 23000:23000 --name u_group1_storage1 --link tracker1:tracker1 --link tracker2:tracker2 imlzw/fastdfs-storage-dht
# 172.17.0.5
docker run -dit -p 282:80 -p 23001:23000 --name u_group1_storage2 --link tracker1:tracker1 --link tracker2:tracker2 imlzw/fastdfs-storage-dht
# 172.17.0.5
docker run -dit -p 282:80 -p 23001:23000 --name u_group1_storage2 --link tracker1:tracker1 --link tracker2:tracker2 imlzw/fastdfs-storage-dht
```
�������ip��������Ļ������п��ܻ��������Ҫ�����޸���������ļ����µ������ļ���/etc/fdfs/*,/etc/fdht/*�����ֶ�ֹͣ���ֶ���������

# ���������ֶ�����
�����������Ѿ���������������Ĺ��ܣ������ṩ����������ֹͣ��������start_fdfs��stop_fdfs
