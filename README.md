# PMG-Transports

Bu repo, Proxmox Mail Gateway (PMG) üzerinde farklı domainler için alıcı sunucuların nasıl yapılandırılacağını (transport ayarları) detaylı bir şekilde açıklamaktadır. Transporte, gelen e-postaların belirli domainlere göre doğru alıcı sunuculara yönlendirilmesini sağlar. Bu yapılandırma, e-posta trafiğinin yönetimini kolaylaştırır ve çoklu domain desteği sunar.



## Transports

Sol menü üzerinden Mail proxy >> Transports sayfasına geliyoruz.

![Yeni Proje (1)](https://github.com/user-attachments/assets/498b1fe9-02f4-40d9-82a6-7be24d0ed56e)

 **Alan**         | **Değer Örneği**  | **Açıklama**                                                              |
|-------------------|-------------------|----------------------------------------------------------------------------|
| **Relay Domain**  | `test.com`        | Gelen e-postaların yönlendirileceği domain.                               |
| **Host**          | `mail.test.com`   | Bu domain için kullanılan alıcı (relay) sunucu.                          |
| **Protocol**      | `SMTP`            | PMG'nin alıcı sunucuyla iletişim kurmak için kullandığı protokol (genelde SMTP). |
| **Port**          | `25`              | Alıcı sunucuya bağlanmak için kullanılan port (varsayılan: 25).           |
| **Use MX**        | `false`           | Eğer bu seçenek etkinse, relay domain için DNS'teki MX kayıtları kullanılır. |
| **Comment**       | (Boş)             | Bu alana, kayıt hakkında açıklama eklenebilir (örneğin: "Test için yapılandırma"). |


Burada, yeni bir transport kuralı eklemek için Ekle (Add) butonuna tıklayın. Açılan pencerede, gelen e-postaların hangi domain için hangi alıcı sunucuya (relay) iletileceğini belirlemek üzere ilgili alanları doldurun. Örneğin, test.com domainine gelen tüm e-postaların mail.test.com sunucusuna iletilmesini istiyorsanız, bu bilgileri doğru şekilde girin ve kaydedin. Bu işlemden sonra, Proxmox Mail Gateway otomatik olarak test.com için gelen tüm e-postaları belirtilen relay sunucusuna yönlendirecektir.

 **Not:** Relay Domains sayfası üzerinden işlem yapılacak olan domaini eklemeyi unutmayınız.


 ## Relaying ve Transport İşlemlerinin Farkı

Relaying ve Transport, her ikisi de e-posta yönlendirme ile ilgilidir, ancak kullanım amaçları ve işlevleri farklıdır:

### Relaying Nedir?
Relaying, bir e-posta sunucusunun gelen veya giden e-postaları başka bir sunucuya iletmesidir. Genellikle giden e-postalar için kullanılır. Örneğin, şirketinizdeki tüm kullanıcıların giden e-postalarını bir SMTP relay sunucusu üzerinden yönlendirmek isteyebilirsiniz. Bu, genelde güvenilirlik ve güvenlik politikaları için yapılır.
Relaying işlemi şu durumlarda kullanılır:

- PMG’nin, giden e-postaları bir SMTP relay sunucusuna göndermesi.
- E-posta gönderimi sırasında IP adresinin gizlenmesi veya birden fazla e-posta sunucusu arasında güvenli bir bağlantı sağlanması.
