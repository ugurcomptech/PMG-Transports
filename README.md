# PMG-Transports

Bu repo, Proxmox Mail Gateway (PMG) üzerinde farklı domainler için alıcı sunucuların nasıl yapılandırılacağını (transport ayarları) detaylı bir şekilde açıklamaktadır. Transporte, gelen e-postaların belirli domainlere göre doğru alıcı sunuculara yönlendirilmesini sağlar. Bu yapılandırma, e-posta trafiğinin yönetimini kolaylaştırır ve çoklu domain desteği sunar.



## Transports

Sol menü üzerinden Mail proxy >> Transports sayfasına geliyoruz.

![image](https://github.com/user-attachments/assets/db0d829e-0db4-4e9f-b786-052545502ade)

 **Alan**         | **Değer Örneği**  | **Açıklama**                                                              |
|-------------------|-------------------|----------------------------------------------------------------------------|
| **Relay Domain**  | `test.com`        | Gelen e-postaların yönlendirileceği domain.                               |
| **Host**          | `mail.test.com`   | Bu domain için kullanılan alıcı (relay) sunucu.                          |
| **Protocol**      | `SMTP`            | PMG'nin alıcı sunucuyla iletişim kurmak için kullandığı protokol (genelde SMTP). |
| **Port**          | `25`              | Alıcı sunucuya bağlanmak için kullanılan port (varsayılan: 25).           |
| **Use MX**        | `false`           | Eğer bu seçenek etkinse, relay domain için DNS'teki MX kayıtları kullanılır. |
| **Comment**       | (Boş)             | Bu alana, kayıt hakkında açıklama eklenebilir (örneğin: "Test için yapılandırma"). |
