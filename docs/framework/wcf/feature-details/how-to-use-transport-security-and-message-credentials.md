---
title: 'Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
author: BrucePerlerMS
ms.openlocfilehash: 40fe7b1fa6a61b56d5dfdde75a92834f096a8be4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082757"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv
Zabezpečení služby pomocí přihlašovacích údajů k přenosu a zprávy používá nejlepší režimy dopravy a zprávu zabezpečení ve Windows Communication Foundation (WCF). V sum transport layer security poskytuje integritu a důvěrnost, zpráva vrstvy zabezpečení poskytuje širokou škálu přihlašovací údaje, které nejsou možné s mechanismy zabezpečení striktní přenosu. Toto téma popisuje základní kroky pro implementaci přenosu pomocí přihlašovacích údajů zprávy <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> vazby. Další informace o nastavení režimu zabezpečení rozhraní najdete v tématu [postupy: nastavení režimu zabezpečení rozhraní](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Pokud nastavení režimu zabezpečení rozhraní `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy. Pro protokol HTTP je mechanismus vrstvy SSL (Secure Sockets) přes HTTP (HTTPS); pro protokol TCP je protokol SSL přes TCP nebo Windows.  
  
 Pokud je přenos protokolu HTTP (pomocí <xref:System.ServiceModel.WSHttpBinding>), SSL přes protokol HTTP poskytuje zabezpečení transportní vrstvy. V takovém případě musíte nakonfigurovat počítač, který je hostitelem služby s certifikátem SSL, který je vázán k portu, jak je uvedeno dále v tomto tématu.  
  
 Pokud je přenos TCP (pomocí <xref:System.ServiceModel.NetTcpBinding>), ve výchozím nastavení zabezpečení transportní vrstvy, které jsou k dispozici je Windows zabezpečení nebo SSL přes protokol TCP. Při použití protokolu SSL přes TCP, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> způsob, jak je uvedeno dále v tomto tématu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Pro účely Proces WSHttpBinding s certifikátem zabezpečení přenosu (v kódu)  
  
1.  Použijte nástroj HttpCfg.exe vytvořit vazbu certifikátu SSL s portem v počítači. Další informace najdete v tématu [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavit <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost na odpovídající hodnotu. (Další informace najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4.  Vytvoření instance <xref:System.Uri> třídy s příslušnou základní adresu. Všimněte si, že adresa musí používat schéma "HTTPS" a musí obsahovat skutečný název počítače a číslo portu, který certifikát SSL je vázán na. (Alternativně můžete nastavit základní adresu v konfiguraci.)  
  
5.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
6.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> a volat <xref:System.ServiceModel.ICommunicationObject.Open%2A> způsob, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Pro účely NetTcpBinding s certifikátem zabezpečení přenosu (v kódu)  
  
1.  Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> třídy a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
3.  Vytvoření instance <xref:System.Uri> třídy s příslušnou základní adresu. Všimněte si, že adresu musí používat schéma "net.tcp". (Alternativně můžete nastavit základní adresu v konfiguraci.)  
  
4.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy.  
  
5.  Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavit certifikát X.509 pro službu.  
  
6.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
7.  Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> způsob, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Použít NetTcpBinding s Windows pro zabezpečení přenosu (v kódu)  
  
1.  Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> třídy a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Nastavení zabezpečení přenosu pomocí nastavení Windows <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> k <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Všimněte si, že se jedná o výchozí nastavení.)  
  
3.  Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4.  Vytvoření instance <xref:System.Uri> třídy s příslušnou základní adresu. Všimněte si, že adresu musí používat schéma "net.tcp". (Alternativně můžete nastavit základní adresu v konfiguraci.)  
  
5.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy.  
  
6.  Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavit certifikát X.509 pro službu.  
  
7.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
8.  Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> způsob, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Pomocí konfigurace  
  
#### <a name="to-use-the-wshttpbinding"></a>Chcete-li použít vazba WSHttpBinding  
  
1.  Konfigurace počítače s certifikátem SSL, který je vázán na port. (Další informace najdete v tématu [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Není nutné nastavovat <`transport`> Hodnota elementu s touto konfigurací.  
  
2.  Určení typu pověření klienta pro zprávy úroveň zabezpečení. Následující příklad nastaví `clientCredentialType` atribut <`message`> element `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Pro účely NetTcpBinding s certifikátem zabezpečení přenosu  
  
1.  Pro protokol SSL přes TCP, je nutné explicitně zadat certifikát `<behaviors>` elementu. Certifikát vystavitele ve výchozím umístění úložiště (místní počítač a osobních úložišť) v následujícím příkladu.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Přidat [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do části vazby  
  
3.  Přidejte prvek vazby a nastavte `name` atribut na odpovídající hodnotu.  
  
4.  Přidat <`security`> element a nastavte `mode` atribut `TransportWithMessageCredential`.  
  
5.  Přidat <`message>` elementu a nastavte `clientCredentialType` atribut na odpovídající hodnotu.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Použít NetTcpBinding s Windows pro zabezpečení přenosu  
  
1.  Přidat [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do části vazby  
  
2.  Přidat <`binding`> element a nastavte `name` atribut na odpovídající hodnotu.  
  
3.  Přidat <`security`> element a nastavte `mode` atribut `TransportWithMessageCredential`.  
  
4.  Přidat <`transport`> element a nastavte `clientCredentialType` atribut `Windows`.  
  
5.  Přidat <`message`> element a nastavte `clientCredentialType` atribut na odpovídající hodnotu. Následující kód nastaví hodnotu k certifikátu.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Nastavení režimu zabezpečení](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
