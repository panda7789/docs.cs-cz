---
title: 'Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv'
description: Naučte se implementovat zabezpečení přenosu s přihlašovacími údaji pro zprávy, které nabízí nejlepší přenos a režimy zabezpečení zpráv ve službě WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246646"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv
Zabezpečení služby pomocí přenosu a přihlašovacích údajů pro zprávy využívá nejlepší z přenosů i režimů zabezpečení zpráv v Windows Communication Foundation (WCF). Zabezpečení transportní vrstvy zajišťuje integritu a důvěrnost, zatímco zabezpečení vrstev zpráv poskytuje celou řadu přihlašovacích údajů, které nejsou možné s přísným mechanismem zabezpečení přenosu. V tomto tématu se dozvíte o základních krocích pro implementaci přenosu s přihlašovacími údaji zprávy pomocí <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> vazeb a. Další informace o nastavení režimu zabezpečení naleznete v tématu [How to: set a Security Mode](../how-to-set-the-security-mode.md).  
  
 Při nastavení režimu zabezpečení na `TransportWithMessageCredential` je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu. V případě protokolu HTTP je mechanismus SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP (HTTPS); v případě protokolu TCP se jedná o protokol SSL přes TCP nebo Windows.  
  
 Pokud je přenos HTTP (pomocí <xref:System.ServiceModel.WSHttpBinding> ), SSL over HTTP poskytuje zabezpečení na úrovni přenosu. V takovém případě je nutné nakonfigurovat počítač hostující službu s certifikátem SSL vázaným na port, jak je uvedeno dále v tomto tématu.  
  
 Pokud je přenos TCP (pomocí <xref:System.ServiceModel.NetTcpBinding> ), ve výchozím nastavení je poskytnuté zabezpečení na úrovni přenosu Windows Security nebo SSL přes TCP. Pokud používáte protokol SSL přes protokol TCP, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak je uvedeno dále v tomto tématu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Použití WSHttpBinding s certifikátem pro zabezpečení přenosu (v kódu)  
  
1. Pomocí nástroje HttpCfg.exe navažte certifikát SSL s portem v počítači. Další informace najdete v tématu [Postup: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
3. Nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost na odpovídající hodnotu. (Další informace najdete v tématu [Výběr typu přihlašovacích údajů](selecting-a-credential-type.md).) Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4. Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou. Upozorňujeme, že adresa musí používat schéma HTTPS a musí obsahovat skutečný název počítače a číslo portu, ke kterému je certifikát SSL vázaný. (Případně můžete v konfiguraci nastavit základní adresu.)  
  
5. Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
6. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> a zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Použití NetTcpBinding s certifikátem pro zabezpečení přenosu (v kódu)  
  
1. Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a nastavte <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. Nastavte na <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
3. Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou. Upozorňujeme, že adresa musí používat schéma NET. TCP. (Případně můžete v konfiguraci nastavit základní adresu.)  
  
4. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.  
  
5. Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavte certifikát X. 509 pro službu.  
  
6. Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
7. Zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Použití NetTcpBinding se systémem Windows pro zabezpečení přenosu (v kódu)  
  
1. Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a nastavte <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. Nastavte zabezpečení přenosu pro použití Windows nastavením na <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.TcpClientCredentialType.Windows> . (Všimněte si, že toto je výchozí nastavení.)  
  
3. Nastavte na <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpovídající hodnotu. Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.  
  
4. Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou. Upozorňujeme, že adresa musí používat schéma NET. TCP. (Případně můžete v konfiguraci nastavit základní adresu.)  
  
5. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.  
  
6. Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavte certifikát X. 509 pro službu.  
  
7. Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
8. Zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Použití konfigurace  
  
#### <a name="to-use-the-wshttpbinding"></a>Použití WSHttpBinding  
  
1. Nakonfigurujte počítač s certifikátem SSL vázaným na port. (Další informace najdete v tématu [Postup: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)). V této konfiguraci není nutné nastavovat `transport` hodnotu prvku <>.  
  
2. Zadejte typ přihlašovacích údajů klienta pro zabezpečení na úrovni zprávy. Následující příklad nastaví `clientCredentialType` atribut `message` prvku <> na `UserName` .  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Použití NetTcpBinding s certifikátem pro zabezpečení přenosu  
  
1. Pro protokol SSL přes TCP musíte explicitně zadat certifikát v `<behaviors>` elementu. Následující příklad určuje certifikát vystavitelem ve výchozím umístění úložiště (místní počítač a osobní úložiště).  
  
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
  
2. Přidat [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do oddílu Bindings  
  
3. Přidejte prvek vazby a nastavte `name` atribut na odpovídající hodnotu.  
  
4. Přidejte prvek <`security`> a nastavte `mode` atribut na `TransportWithMessageCredential` .  
  
5. Přidejte prvek <`message>` a nastavte `clientCredentialType` atribut na odpovídající hodnotu.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Použití NetTcpBinding s Windows pro zabezpečení přenosu  
  
1. Přidejte [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do části Bindings (vazby),  
  
2. Přidejte prvek <`binding`> a nastavte `name` atribut na odpovídající hodnotu.  
  
3. Přidejte prvek <`security`> a nastavte `mode` atribut na `TransportWithMessageCredential` .  
  
4. Přidejte prvek <`transport`> a nastavte `clientCredentialType` atribut na `Windows` .  
  
5. Přidejte prvek <`message`> a nastavte `clientCredentialType` atribut na odpovídající hodnotu. Následující kód nastaví hodnotu na certifikát.  
  
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

- [Postupy: Nastavení režimu zabezpečení](../how-to-set-the-security-mode.md)
- [Zabezpečení služeb](../securing-services.md)
- [Zabezpečení služeb a klientů](securing-services-and-clients.md)
