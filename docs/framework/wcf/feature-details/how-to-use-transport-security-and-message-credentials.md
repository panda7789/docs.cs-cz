---
title: 'Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: 11
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: fad7970711435cdabecd883f5e1dc44c64bd2c93
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv
Zabezpečení služby přenosu a zpráva pověření používá nejlepší režimy zabezpečení přenosu a zpráv v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Transport layer security poskytuje v sum, integrity a důvěrnosti, zatímco zpráva vrstvy zabezpečení poskytuje přihlašovací údaje, které nejsou možné pomocí mechanismy zabezpečení striktní přenosu. Toto téma ukazuje základní kroky pro implementaci přenosu zpráv přihlašovací údaje pomocí <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> vazby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] nastavení režimu zabezpečení, najdete v části [postupy: nastavení režimu zabezpečení](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Při nastavování režimu zabezpečení na `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy. Pro protokol HTTP je tento mechanismus Secure Sockets Layer (SSL) přes protokol HTTP (HTTPS); pro TCP je protokol SSL přes TCP nebo systému Windows.  
  
 Pokud je přenos HTTP (pomocí <xref:System.ServiceModel.WSHttpBinding>), SSL přes protokol HTTP poskytuje zabezpečení transportní vrstvy. V takovém případě musíte nakonfigurovat počítač hostující službu certifikátem SSL vázána k portu, jak uvidíte později v tomto tématu.  
  
 Pokud je přenos TCP (pomocí <xref:System.ServiceModel.NetTcpBinding>), ve výchozím nastavení zabezpečení transportní vrstvy poskytované je zabezpečení systému Windows nebo SSL přes protokol TCP. Při použití protokolu SSL přes TCP, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metoda, jak uvidíte později v tomto tématu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Použít WSHttpBinding s certifikátem zabezpečení přenosu (v kódu)  
  
1.  Použijte nástroj HttpCfg.exe k vytvoření vazby certifikátu SSL port na počítači. Další informace najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> a nastavit <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost na odpovídající hodnotu. (Další informace najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4.  Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu. Všimněte si, že adresa musí používat schéma "HTTPS" a musí obsahovat skutečný název počítač a číslo portu, který je vázána certifikát SSL. (Alternativně můžete nastavit základní adresa v konfiguraci.)  
  
5.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.  
  
6.  Vytvořte instanci <xref:System.ServiceModel.ServiceHost> a volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Použít NetTcpBinding s certifikátem zabezpečení přenosu (v kódu)  
  
1.  Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
3.  Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu. Všimněte si, že adresu musí používat schéma "net.tcp". (Alternativně můžete nastavit základní adresa v konfiguraci.)  
  
4.  Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.  
  
5.  Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třída explicitně nastavit pro službu certifikát X.509.  
  
6.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.  
  
7.  Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Pro použití NetTcpBinding s Windows pro zabezpečení přenosu (v kódu)  
  
1.  Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Nastavení zabezpečení přenosu pomocí systému Windows nastavením <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> k <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Všimněte si, že toto je výchozí hodnota.)  
  
3.  Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4.  Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu. Všimněte si, že adresu musí používat schéma "net.tcp". (Alternativně můžete nastavit základní adresa v konfiguraci.)  
  
5.  Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.  
  
6.  Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třída explicitně nastavit pro službu certifikát X.509.  
  
7.  Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.  
  
8.  Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Pomocí konfigurace  
  
#### <a name="to-use-the-wshttpbinding"></a>Chcete-li použít WSHttpBinding  
  
1.  Nakonfigurujte počítač certifikátem SSL vázány na port. (Další informace najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Není nutné nastavovat <`transport`> Hodnota elementu s touto konfigurací.  
  
2.  Zadejte typ pověření klienta pro zprávy úroveň zabezpečení. Následující příklad nastavuje `clientCredentialType` atribut <`message`> elementu, který chcete `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Použít NetTcpBinding s certifikátem zabezpečení přenosu  
  
1.  Pro protokol SSL přes TCP, je třeba explicitně zadat certifikát v `<behaviors>` elementu. Následující příklad určuje certifikát jeho vystavitelem ve výchozím umístění úložiště (místní počítač a osobní úložiště).  
  
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
  
3.  Přidá prvek vazby a nastavte `name` atribut na odpovídající hodnotu.  
  
4.  Přidat <`security`> elementu a nastavte `mode` atribut `TransportWithMessageCredential`.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Pro použití NetTcpBinding s Windows pro zabezpečení přenosu  
  
1.  Přidat [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do části vazby  
  
2.  Přidat <`binding`> elementu a sadu `name` atribut na odpovídající hodnotu.  
  
3.  Přidat <`security`> elementu a nastavte `mode` atribut `TransportWithMessageCredential`.  
  
4.  Přidat <`transport`> elementu a sadu `clientCredentialType` atribut `Windows`.  
  
5.  Přidat <`message`> elementu a sadu `clientCredentialType` atribut na odpovídající hodnotu. Následující kód nastaví hodnotu k certifikátu.  
  
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
