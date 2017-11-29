---
title: "Postupy: Nastavení režimu zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 595999bfa7d3472fc31274a0c9652af5416d2da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-security-mode"></a>Postupy: Nastavení režimu zabezpečení
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]zabezpečení má tři běžné režimy zabezpečení, které se nacházejí na nejvíce předdefinované vazby: přenos zpráv a "přenos s pověřením zpráv." Dva další režimy, které jsou specifické pro dvě vazby: v režimu "pouze přenos pověření" nalezen <xref:System.ServiceModel.BasicHttpBinding>a "I" režim, v nalezen <xref:System.ServiceModel.NetMsmqBinding>. Ale v tomto tématu soustřeďuje na tři běžných režimů zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, a <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Všimněte si, že ne každé předdefinované vazba podporuje všechny tyto režimy. Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> třídy a ukazuje, jak nastavení režimu prostřednictvím kódu programu i prostřednictvím konfigurace.  
  
 [!INCLUDE[crabout](../../../includes/crdefault-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zabezpečení, najdete v části [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpečení služby](../../../docs/framework/wcf/securing-services.md), a [zabezpečení služeb a klientů](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]přenosu režim a zpráv najdete v tématu [zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md) a [zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Nastavení režimu zabezpečení v kódu  
  
1.  Vytvoření instance třídy vazby, kterou používáte. Seznam předdefinovaných vazby najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.  
  
2.  Nastavte `Mode` vlastnost v objektu vrácený `Security` vlastnost.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Alternativně nastavte režim na zprávu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Nebo můžete nastavit režim přenosu s pověřením zpráv, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Nastavení vlastnosti ClientCredentialType  
 Nastavení režimu na jednu ze tří hodnot Určuje, jak nastavit `ClientCredentialType` vlastnost. Například pomocí <xref:System.ServiceModel.WSHttpBinding> třída, nastavení režimu na `Transport` znamená, je nutné nastavit <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třída na odpovídající hodnotu.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Chcete-li nastavit vlastnost ClientCredentialType pro režim přenosu  
  
1.  Vytvoření instance vazby.  
  
2.  Nastavte `Mode` vlastnost `Transport`.  
  
3.  Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Chcete-li nastavit vlastnost ClientCredentialType pro režim zprávy  
  
1.  Vytvoření instance vazby.  
  
2.  Nastavte `Mode` vlastnost `Message`.  
  
3.  Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Chcete-li nastavit vlastnost režimu a ClientCredentialType v konfiguraci  
  
1.  Přidat element do odpovídající vazby [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru. Následující příklad přidá [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.  
  
2.  Přidat `<binding>` elementu a sadu jeho `name` atribut na odpovídající hodnotu.  
  
3.  Přidat `<security>` elementu a sadu `mode` atribut `Message`, `Transport`, nebo `TransportWithMessageCredential`.  
  
4.  Pokud režim je nastaven na `Transport`, přidejte `<transport>` elementu a sadu `clientCredential` atribut na odpovídající hodnotu.  
  
     Následující příklad nastaví režim "`Transport"`a nastaví `clientCredentialType` atribut `<transport>` element"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Alternativně nastavte `security mode` na "`Message"`, za nímž následují `<"message">` elementu. Tento příklad nastaví `clientCredentialType` na "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Pomocí <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> hodnota je zvláštní případ a je popsáno níže.  
  
### <a name="using-transportwithmessagecredential"></a>Pomocí TransportWithMessageCredential  
 Při nastavování režimu zabezpečení na `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy. Například protokol HTTP používá Secure Sockets Layer (SSL) přes protokol HTTP (HTTPS). Proto nastavení `ClientCredentialType` vlastnost libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity>) je ignorována.  Jinými slovy, můžete nastavit pouze `ClientCredentialType` objektu zabezpečení zpráv (pro `WSHttpBinding` vazba, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Postupy: použití zabezpečení přenosu a přihlašovací údaje zpráva](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace portu certifikát protokolu SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Postupy: použití zabezpečení přenosu a přihlašovací údaje zpráva](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [\<zabezpečení >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
