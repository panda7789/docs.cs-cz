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
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320899"
---
# <a name="how-to-set-the-security-mode"></a>Postupy: Nastavení režimu zabezpečení

Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy. Dva další režimy jsou specifické pro dvě vazby: režim "přenos – pouze přihlašovací údaje", který se nachází na <xref:System.ServiceModel.BasicHttpBinding> a v režimu "obojí", který se nachází na <xref:System.ServiceModel.NetMsmqBinding>. Toto téma se však zaměřuje na tři běžné režimy zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> a <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.

Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy. Toto téma nastaví režim s třídami <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.

Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](./feature-details/security-overview.md), zabezpečení [služeb](securing-services.md) [a zabezpečení služeb a klientů](./feature-details/securing-services-and-clients.md). Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](./feature-details/transport-security.md) a [zabezpečení zpráv](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Nastavení režimu zabezpečení v kódu

1. Vytvořte instanci třídy vazby, kterou používáte. Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](system-provided-bindings.md). Tento příklad vytvoří instanci třídy <xref:System.ServiceModel.WSHttpBinding>.

2. Nastavte vlastnost `Mode` objektu vráceného vlastností `Security`.

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

Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje vlastnost `ClientCredentialType`. Například pomocí třídy <xref:System.ServiceModel.WSHttpBinding> nastavíte režim na `Transport` znamená, že musíte nastavit vlastnost <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> třídy <xref:System.ServiceModel.HttpTransportSecurity> na odpovídající hodnotu.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Nastavení vlastnosti ClientCredentialType pro transportní režim

1. Vytvořte instanci vazby.

2. Nastavte vlastnost `Mode` na hodnotu `Transport`.

3. Nastavte vlastnost `ClientCredential` na odpovídající hodnotu. Následující kód nastaví vlastnost na hodnotu `Windows`.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Nastavení vlastnosti ClientCredentialType pro režim zprávy

1. Vytvořte instanci vazby.

2. Nastavte vlastnost `Mode` na hodnotu `Message`.

3. Nastavte vlastnost `ClientCredential` na odpovídající hodnotu. Následující kód nastaví vlastnost na hodnotu `Certificate`.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci

1. Přidejte vhodný element vazby do [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru. Následující příklad přidá prvek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .

2. Přidejte prvek `<binding>` a nastavte jeho atribut `name` na odpovídající hodnotu.

3. Přidejte prvek `<security>` a nastavte atribut `mode` na `Message`, `Transport` nebo `TransportWithMessageCredential`.

4. Pokud je režim nastaven na `Transport`, přidejte prvek `<transport>` a nastavte atribut `clientCredential` na odpovídající hodnotu.

     Následující příklad nastaví režim na "`Transport"` a poté nastaví atribut `clientCredentialType` prvku `<transport>` na hodnotu" `Windows"` ".

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Případně nastavte `security mode` na "`Message"`" následovaný elementem `<"message">`. Tento příklad nastaví `clientCredentialType` na "`Certificate"`.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Použití hodnoty <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> je zvláštní případ a je vysvětleno níže.

### <a name="using-transportwithmessagecredential"></a>Použití TransportWithMessageCredential

Když nastavíte režim zabezpečení na `TransportWithMessageCredential`, Transport určí skutečný mechanismus, který poskytuje zabezpečení na úrovni přenosu. Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS). Proto se nastavení vlastnosti `ClientCredentialType` libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity>) ignoruje.  Jinými slovy můžete nastavit pouze `ClientCredentialType` objektu zabezpečení zprávy (pro vazbu `WSHttpBinding`, objekt <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).

Další informace najdete v tématu [Postupy: použití zabezpečení přenosu a přihlašovacích údajů pro zprávy](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace portu s certifikátem SSL](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpečení přenosu](./feature-details/transport-security.md)
- [Zabezpečení zpráv](./feature-details/message-security-in-wcf.md)
- [Přehled zabezpečení](./feature-details/security-overview.md)
- [Vazby poskytované systémem](system-provided-bindings.md)
- [@no__t – 1security >](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [@no__t – 1security >](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [@no__t – 1security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
