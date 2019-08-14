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
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971979"
---
# <a name="how-to-set-the-security-mode"></a>Postupy: Nastavení režimu zabezpečení

Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy. Dva další režimy jsou specifické pro dvě vazby: režim "přenos pouze s přihlašovacími údaji" <xref:System.ServiceModel.BasicHttpBinding>, který se nachází v systému, a režim "obojí", který se nachází <xref:System.ServiceModel.NetMsmqBinding>v. Toto téma se však zaměřuje na tři běžné režimy zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>a.

Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy. Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> třídami a a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.

Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md), zabezpečení [služeb](../../../docs/framework/wcf/securing-services.md) [a zabezpečení služeb a klientů](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md) a [zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Nastavení režimu zabezpečení v kódu

1. Vytvořte instanci třídy vazby, kterou používáte. Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md). Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.

2. Nastavte vlastnost objektu vráceného `Security`vlastností. `Mode`

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

Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje `ClientCredentialType` vlastnost. Například použití <xref:System.ServiceModel.WSHttpBinding> třídy, nastavení režimu na `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> znamená, že musíte <xref:System.ServiceModel.HttpTransportSecurity> nastavit vlastnost třídy na odpovídající hodnotu.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Nastavení vlastnosti ClientCredentialType pro transportní režim

1. Vytvořte instanci vazby.

2. Nastavte `Mode` vlastnost `Transport`.

3. `ClientCredential` Nastavte vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na `Windows`hodnotu.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Nastavení vlastnosti ClientCredentialType pro režim zprávy

1. Vytvořte instanci vazby.

2. Nastavte `Mode` vlastnost `Message`.

3. `ClientCredential` Nastavte vlastnost na odpovídající hodnotu. Následující kód nastaví vlastnost na `Certificate`hodnotu.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci

1. Přidejte příslušný prvek vazby do [ \<prvku > vazby](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru. Následující příklad přidá [ \<prvek WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .

2. Přidejte element a nastavte jeho `name` atribut na odpovídající hodnotu. `<binding>`

3. `mode` `Message`Přidejte element a nastavte atribut na, `Transport`, nebo `TransportWithMessageCredential`. `<security>`

4. Pokud je režim nastaven na `Transport`, `<transport>` přidejte element a nastavte `clientCredential` atribut na odpovídající hodnotu.

     Následující příklad nastaví`Transport"`režim na "a poté `clientCredentialType` nastaví atribut `<transport>` elementu na"`Windows"`.

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Případně nastavte `security mode` na ""`Message"`, následované `<"message">` prvkem. V `clientCredentialType` tomto příkladu se nastaví`Certificate"`na.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Použití hodnoty je zvláštní případ a je vysvětleno níže.

### <a name="using-transportwithmessagecredential"></a>Použití TransportWithMessageCredential

Při nastavení režimu zabezpečení na `TransportWithMessageCredential`je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu. Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS). Proto se nastavení `ClientCredentialType` vlastnosti libovolného objektu zabezpečení přenosu ( <xref:System.ServiceModel.HttpTransportSecurity>například) ignoruje.  Jinými slovy můžete nastavit `ClientCredentialType` pouze objekt zabezpečení zprávy ( `WSHttpBinding` pro vazbu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).

Další informace najdete v tématu [jak: Použijte zabezpečení přenosu a přihlašovací údaje](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)pro zprávy.

## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace portu s certifikátem SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Použít zabezpečení přenosu a přihlašovací údaje pro zprávy](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<> zabezpečení](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<> zabezpečení](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<> zabezpečení](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
