---
title: 'Postupy: Nastavení režimu zabezpečení'
description: 'Naučte se, jak nastavit tři běžné režimy zabezpečení WCF u většiny předdefinovaných vazeb: přenos, zpráva a TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244540"
---
# <a name="how-to-set-the-security-mode"></a>Postupy: Nastavení režimu zabezpečení

Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy. Dva další režimy jsou specifické pro dvě vazby: režim "přenos pouze s přihlašovacími údaji", který se nachází v systému <xref:System.ServiceModel.BasicHttpBinding> , a režim "obojí", který se nachází v <xref:System.ServiceModel.NetMsmqBinding> . Toto téma se však zaměřuje na tři běžné režimy zabezpečení:, a <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .

Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy. Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> třídami a a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.

Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](./feature-details/security-overview.md), zabezpečení [služeb](securing-services.md) [a zabezpečení služeb a klientů](./feature-details/securing-services-and-clients.md). Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](./feature-details/transport-security.md) a [zabezpečení zpráv](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Nastavení režimu zabezpečení v kódu

1. Vytvořte instanci třídy vazby, kterou používáte. Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](system-provided-bindings.md). Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.

2. Nastavte `Mode` vlastnost objektu vráceného `Security` vlastností.

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     Případně můžete nastavit režim na zprávu, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     Nebo nastavte režim pro přenos s přihlašovacími údaji zprávy, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a>Nastavení vlastnosti ClientCredentialType

Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje `ClientCredentialType` vlastnost. Například použití <xref:System.ServiceModel.WSHttpBinding> třídy, nastavení režimu na `Transport` znamená, že musíte nastavit <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třídy na odpovídající hodnotu.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Nastavení vlastnosti ClientCredentialType pro transportní režim

1. Vytvořte instanci vazby.

2. Nastavte `Mode` vlastnost na hodnotu `Transport` .

3. Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na hodnotu `Windows` .

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Nastavení vlastnosti ClientCredentialType pro režim zprávy

1. Vytvořte instanci vazby.

2. Nastavte `Mode` vlastnost na hodnotu `Message` .

3. Nastavte `ClientCredential` vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na hodnotu `Certificate` .

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci

1. Přidejte vhodný element vazby do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru. Následující příklad přidá [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) prvek.

2. Přidejte `<binding>` element a nastavte jeho `name` atribut na odpovídající hodnotu.

3. Přidejte `<security>` element a nastavte `mode` atribut na `Message` , `Transport` , nebo `TransportWithMessageCredential` .

4. Pokud je režim nastaven na `Transport` , přidejte `<transport>` element a nastavte `clientCredential` atribut na odpovídající hodnotu.

     Následující příklad nastaví režim na " `Transport"` a poté nastaví `clientCredentialType` atribut `<transport>` elementu na" `Windows"` .

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Případně nastavte na `security mode` "" `Message"` , následované `<"message">` prvkem. V tomto příkladu se nastaví `clientCredentialType` na `Certificate"` .

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Použití <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> hodnoty je zvláštní případ a je vysvětleno níže.

### <a name="using-transportwithmessagecredential"></a>Použití TransportWithMessageCredential

Při nastavení režimu zabezpečení na `TransportWithMessageCredential` je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu. Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS). Proto `ClientCredentialType` se nastavení vlastnosti libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity> ) ignoruje.  Jinými slovy můžete nastavit pouze `ClientCredentialType` objekt zabezpečení zprávy (pro `WSHttpBinding` vazbu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).

Další informace najdete v tématu [Postupy: použití zabezpečení přenosu a přihlašovacích údajů pro zprávy](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Viz také

- [Postupy: Konfigurace portu s certifikátem SSL](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpečení přenosu](./feature-details/transport-security.md)
- [Zabezpečení zpráv](./feature-details/message-security-in-wcf.md)
- [Přehled zabezpečení](./feature-details/security-overview.md)
- [Vazby poskytované systémem](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
