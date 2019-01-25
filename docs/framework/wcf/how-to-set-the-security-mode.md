---
title: 'Postupy: Nastavení režimu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: c5e6d26fd665fa750b5608002d7abc938075a6ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663034"
---
# <a name="how-to-set-the-security-mode"></a>Postupy: Nastavení režimu zabezpečení
Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí na nejvíce předdefinovaných vazeb: přenos zpráv a "přenos s přihlašovacími údaji zprávy." Další dva režimy jsou specifické pro dvě vazby: v režimu "pouze přenosu credential" nalezen <xref:System.ServiceModel.BasicHttpBinding>a "I" režim na <xref:System.ServiceModel.NetMsmqBinding>. Ale v tomto tématu se soustřeďuje na tři běžných režimů zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, a <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Všimněte si, že ne každé předdefinované vazba podporuje všechny tyto režimy. Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> třídy a ukazuje, jak se nastavení režimu prostřednictvím kódu programu i prostřednictvím konfigurace.  
  
 Další informace najdete v části zabezpečení WCF, naleznete v tématu [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpečení služby](../../../docs/framework/wcf/securing-services.md), a [zabezpečení služeb a klientů](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Další informace o režimu přenosu a zpráv, najdete v části [zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md) a [zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Nastavení režimu zabezpečení v kódu  
  
1.  Vytvoření instance třídy vazby, kterou používáte. Seznam předdefinovaných vazeb, najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). Tento příklad vytvoří instance <xref:System.ServiceModel.WSHttpBinding> třídy.  
  
2.  Nastavte `Mode` vlastnosti objektů vrácené objektem `Security` vlastnost.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Alternativně nastavte režim na zprávu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Nebo nastavte režim přenosu s přihlašovacími údaji zprávy, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Můžete také nastavit režim v konstruktoru vazbu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Nastavení vlastnosti ClientCredentialType  
 Nastavení režimu na jednu ze tří hodnot Určuje, jak nastavit `ClientCredentialType` vlastnost. Například použití <xref:System.ServiceModel.WSHttpBinding> třídy, nastavení režimu na `Transport` znamená, že je nutné nastavit <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třídy na odpovídající hodnotu.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Chcete-li nastavit vlastnost nebyl typ ClientCredentialType pro režim přenosu  
  
1.  Vytvoření instance vazby.  
  
2.  Nastavte `Mode` vlastnost `Transport`.  
  
3.  Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Nastavit vlastnost nebyl typ ClientCredentialType pro režim zprávy  
  
1.  Vytvoření instance vazby.  
  
2.  Nastavte `Mode` vlastnost `Message`.  
  
3.  Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Chcete-li nastavit vlastnost režimu a nebyl typ ClientCredentialType v konfiguraci  
  
1.  Přidat element příslušnou datovou vazbu [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru. Následující příklad přidá [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.  
  
2.  Přidat `<binding>` elementu a nastavte jeho `name` atribut na odpovídající hodnotu.  
  
3.  Přidat `<security>` elementu a nastavte `mode` atribut `Message`, `Transport`, nebo `TransportWithMessageCredential`.  
  
4.  Pokud je nastavené na `Transport`, přidejte `<transport>` elementu a nastavte `clientCredential` atribut na odpovídající hodnotu.  
  
     Následující příklad nastaví režim na "`Transport"`a pak nastaví `clientCredentialType` atribut `<transport>` prvku"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Můžete také nastavit `security mode` na "`Message"`a po něm `<"message">` elementu. Tento příklad nastaví `clientCredentialType` na "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Použití <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> hodnota je zvláštní případ a je popsán níže.  
  
### <a name="using-transportwithmessagecredential"></a>Pomocí TransportWithMessageCredential  
 Pokud nastavení režimu zabezpečení rozhraní `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy. Například protokolu HTTP používá vrstvy SSL (Secure Sockets) přes HTTP (HTTPS). Proto nastavení `ClientCredentialType` vlastnost libovolný objekt zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity>) se ignoruje.  Jinými slovy, lze nastavit pouze `ClientCredentialType` objektu zabezpečení zprávy (pro `WSHttpBinding` vazby <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).  
  
 Další informace najdete v tématu [jak: Zabezpečení přenosu pomocí přihlašovacích údajů a zpráv](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Konfigurace portu s certifikátem SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Zabezpečení přenosu pomocí přihlašovacích údajů a zpráv](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
