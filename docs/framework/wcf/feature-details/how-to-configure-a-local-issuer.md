---
title: 'Postupy: Konfigurace místního vystavitele'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972070"
---
# <a name="how-to-configure-a-local-issuer"></a>Postupy: Konfigurace místního vystavitele

Toto téma popisuje, jak nakonfigurovat klienta tak, aby používal místního vystavitele pro vydané tokeny.

Když klient komunikuje se službou federované služby, je často určena adresa služby tokenu zabezpečení, u které se očekává vystavení tokenu, který bude klient používat k ověření identity pro federované služby. V některých situacích může být klient nakonfigurovaný tak, aby používal *místního*vystavitele.

Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` adresa vydavatele federované vazby nebo. `null` V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresu místního vystavitele a vazbu, která se má použít ke komunikaci s tímto vystavitelem.

> [!NOTE]
> Pokud je `ClientCredentials` `true`vlastnost třídy nastavena na hodnotu, není zadána adresa místního vystavitele a adresa vystavitele [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) , kterou určuje WSFederationHttpBinding > nebo jiná federované vazba, je <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`nebo je`null`, použije se Vystavitel Windows CardSpace.

## <a name="to-configure-the-local-issuer-in-code"></a>Konfigurace místního vystavitele v kódu

1. Vytvořit proměnnou typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnosti `ClientCredentials` třídy. Tato <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> instance je vrácena vlastností klienta (zděděna z <xref:System.ServiceModel.ClientBase%601>) <xref:System.ServiceModel.ChannelFactory>nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnosti:

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Nastavte vlastnost na novou instanci <xref:System.ServiceModel.EndpointAddress>s adresou místního vystavitele jako argument konstruktoru. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders` Parametr je<xref:System.ServiceModel.Channels.AddressHeader> pole instancí, jak je znázorněno na obrázku.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Nastavte vazbu pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnosti.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. Volitelné. Přidejte nakonfigurované chování koncového bodu pro místního vystavitele přidáním takového chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastností.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Konfigurace místního vystavitele v konfiguraci

1. Vytvořte prvek [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) localIssuer > jako podřízený prvek třídy IssuedToken >, který je sám podřízenou položkou prvku ClientCredentials > v chování koncového bodu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)

2. `address` Nastavte atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.

3. Nastavte atributy `bindingConfiguration` a na hodnoty, které odkazují na příslušnou vazbu, která se má použít při komunikaci s místním koncovým bodem vystavitele. `binding`

4. Volitelné. Nastavte prvek`localIssuer`identity > jako podřízený prvek elementu < > a určete informace o identitě pro místního vystavitele. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

5. Volitelné. `localIssuer` [ Nastavte>elementHeadersjakopodřízenýprvekelementu<>aurčetedalšíhlavičky,kteréjsoupožadoványprosprávnéadresovánímístního\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) vystavitele.

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Všimněte si, že pokud je pro danou vazbu určena adresa vydavatele a vazba, místní vystavitel není použit pro koncové body, které používají tuto vazbu. Klienti, kteří očekávají, že mají vždy používat místního vystavitele, by měli zajistit, aby nepoužívali takovou vazbu ani nezměnili vazbu tak, `null`aby byla adresa vystavitele.

## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
