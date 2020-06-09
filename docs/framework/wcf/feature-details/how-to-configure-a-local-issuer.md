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
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601241"
---
# <a name="how-to-configure-a-local-issuer"></a>Postupy: Konfigurace místního vystavitele

Toto téma popisuje, jak nakonfigurovat klienta tak, aby používal místního vystavitele pro vydané tokeny.

Když klient komunikuje se službou federované služby, je často určena adresa služby tokenu zabezpečení, u které se očekává vystavení tokenu, který bude klient používat k ověření identity pro federované služby. V některých situacích může být klient nakonfigurovaný tak, aby používal *místního vystavitele*.

Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je adresa vydavatele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null` . V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresu místního vystavitele a vazbu, která se má použít ke komunikaci s tímto vystavitelem.

> [!NOTE]
> Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` je vlastnost třídy nastavena na hodnotu `true` , není zadána adresa místního vystavitele a adresa vystavitele, která je určena v [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo jiné federované vazbě `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` , je, nebo, pak je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` použit Vystavitel Windows CardSpace.

## <a name="to-configure-the-local-issuer-in-code"></a>Konfigurace místního vystavitele v kódu

1. Vytvořit proměnnou typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnosti `ClientCredentials` třídy. Tato instance je vrácena <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastností klienta (zděděna z <xref:System.ServiceModel.ClientBase%601> ) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnosti <xref:System.ServiceModel.ChannelFactory> :

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastnost na novou instanci <xref:System.ServiceModel.EndpointAddress> s adresou místního vystavitele jako argument konstruktoru.

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders`Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instancí, jak je znázorněno na obrázku.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Nastavte vazbu pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> Vlastnosti.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. Nepovinný parametr. Přidejte nakonfigurované chování koncového bodu pro místního vystavitele přidáním takového chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastností.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Konfigurace místního vystavitele v konfiguraci

1. Vytvořte [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) prvek jako podřízený [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) prvek prvku, který je podřízeným prvkem [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) prvku v chování koncového bodu.

2. Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.

3. Nastavte `binding` atributy a `bindingConfiguration` na hodnoty, které odkazují na příslušnou vazbu, která se má použít při komunikaci s místním koncovým bodem vystavitele.

4. Nepovinný parametr. Nastavte [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element jako podřízenou položku `localIssuer` prvku <> a zadejte informace o identitě místního vystavitele.

5. Nepovinný parametr. Nastavte [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element jako podřízený `localIssuer` prvek <> a určete další hlavičky, které jsou požadovány pro správné adresování místního vystavitele.

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Všimněte si, že pokud je pro danou vazbu určena adresa vydavatele a vazba, místní vystavitel není použit pro koncové body, které používají tuto vazbu. Klienti, kteří očekávají, že mají vždy používat místního vystavitele, by měli zajistit, aby nepoužívali takovou vazbu ani nezměnili vazbu tak, aby byla adresa vystavitele `null` .

## <a name="see-also"></a>Viz také

- [Postupy: Konfigurace pověření ve službě Federation Service](how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření federovaného klienta](how-to-create-a-federated-client.md)
- [Postupy: Vytvoření WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
