---
title: Programování zabezpečení WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: d327605c084cd5fb1c65fbb786e871b421730b83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313317"
---
# <a name="programming-wcf-security"></a>Programování zabezpečení WCF
Toto téma popisuje základní programovacích úloh umožňuje vytvořit zabezpečenou webovou aplikaci Windows Communication Foundation (WCF). Toto téma popisuje pouze ověřování, důvěrnost a integrita, souhrnně označované jako *přenos zabezpečení*. Toto téma nepopisuje autorizace (řízení přístupu k prostředkům nebo službám); informace o ověřování najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Cenné Úvod k koncepty zabezpečení, zejména ve vztahu WCF, najdete na webu MSDN na sadu vzory a postupy kurzy [scénářů, modely a pokyny k implementaci pro webové služby rozšíření (WSE) 3.0](https://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programování zabezpečení WCF je založena na třech krocích nastavením následující hodnoty: režim zabezpečení, typ přihlašovacích údajů klienta a hodnot přihlašovacích údajů. Provedením těchto kroků prostřednictvím kódu nebo konfigurace.  
  
## <a name="setting-the-security-mode"></a>Nastavení režimu zabezpečení  
 Následující příklad vysvětluje obecné kroky pro programování s režimem zabezpečení ve službě WCF:  
  
1. Vyberte jednu z předdefinovaných vazeb, které jsou vhodné pro vaše požadavky na aplikace. Seznam voleb vazby najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md). Téměř Každá vazba má ve výchozím nastavení povoleno zabezpečení. Jedinou výjimkou je <xref:System.ServiceModel.BasicHttpBinding> třídy (pomocí konfigurace, [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Vazba, kterou vyberete určuje přenos. Například <xref:System.ServiceModel.WSHttpBinding> používá protokol HTTP jako přenosový; <xref:System.ServiceModel.NetTcpBinding> používá protokol TCP.  
  
2. Vyberte jeden z režimů zabezpečení vazby. Mějte na paměti, určuje vazbu, kterou vyberete možnosti režimu k dispozici. Například <xref:System.ServiceModel.WSDualHttpBinding> neumožňuje zabezpečení přenosu (není možné). Podobně ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umožňuje zabezpečení zpráv.  
  
     Máte tři možnosti:  
  
    1.  `Transport`  
  
         Zabezpečení přenosu závisí mechanismus, který používá vazba, kterou jste vybrali. Například, pokud používáte `WSHttpBinding` mechanismus zabezpečení, který je vrstva SSL (Secure Sockets) (taky mechanismus pro protokol HTTPS). Obecně řečeno hlavní výhodou zabezpečení přenosu je, že poskytuje dobrou propustnost bez ohledu na to, které přenosu, kterou používáte. Však obsahuje dvě omezení: První je, že mechanismus přenosu Určuje typ přihlašovacích údajů pro ověření uživatele. Nevýhodou jde jenom v případě, že služba potřebuje pro spolupráci s ostatními službami, které vyžadují různé typy přihlašovacích údajů. Druhým je, že, protože není zabezpečení na úrovni zprávy, zabezpečení je implementována v hop-by-hop způsobem spíše než začátku do konce. Toto druhé omezení je problém pouze v případě, že cesta zpráv mezi klientem a službou obsahuje zprostředkovatelů. Další informace o přenosu, které používat, naleznete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Další informace o použití zabezpečení přenosu, naleznete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         Zabezpečení zpráv znamená, že každá zpráva obsahuje potřebné hlavičky a zabezpečení dat, aby se zprávy. Protože se liší složení záhlaví, může obsahovat libovolný počet přihlašovacích údajů. Faktor to stane, pokud jste se spolupráce s jinými službami vyžadující přihlašovacích údajů konkrétní typ, který nelze uvádět přenosový mechanismus, nebo pokud zpráva musí být použit s víc než jedna služba, kde každá služba vyžaduje typ různých přihlašovacích údajů.  
  
         Další informace najdete v tématu [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Tato volba používá přenosové vrstvy zabezpečení přenosu zpráv, sice zahrnuje všechny zprávy bohaté přihlašovací údaje potřebovat jiné služby. Tím se zkombinuje výkonu výhod zabezpečení přenosu s výhodou formátovaným přihlašovací údaje zabezpečení zpráv. Tato možnost je dostupná následující vazbami: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, a <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Pokud se rozhodnete pro použití zabezpečení přenosu HTTP (jinými slovy, HTTPS), musíte také nakonfigurovat hostitele certifikátem SSL a povolení protokolu SSL na portu. Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Pokud používáte <xref:System.ServiceModel.WSHttpBinding> a není potřeba navázat zabezpečenou relaci, nastavte <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost `false`.  
  
     Zabezpečené relace nastane, pokud klient a služba vytvoření kanálu pomocí symetrického klíče (klient a server používají stejný klíč pro délku konverzaci, dokud není zavřena dialogového okna).  
  
## <a name="setting-the-client-credential-type"></a>Nastavení typu pověření klienta  
 Vyberte typ pověření klienta podle potřeby. Další informace najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). K dispozici jsou následující typy přihlašovacích údajů klienta:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 V závislosti na tom, jak nastavit režim musíte nastavit typ přihlašovacích údajů. Například pokud jste vybrali `wsHttpBinding`a mít nastavte režim na "Zpráva", pak můžete také nastavit `clientCredentialType` atribut elementu zprávy do jedné z následujících hodnot: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak je znázorněno v následujícím příkladu konfigurace.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 Nebo v kódu:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Nastavení hodnot přihlašovacích údajů služby  
 Po výběru typu pověření klienta, je nutné nastavit samotné přihlašovací údaje pro služby a klienti měli používat. Na služby, přihlašovací údaje jsou nastavené pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy a vrácené <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost <xref:System.ServiceModel.ServiceHostBase> třídy. Vazba používá znamená typ přihlašovacích údajů služby, režimu zabezpečení a typu pověření klienta. Následující kód nastaví certifikát přihlašovacích údajů pro služby.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Nastavení hodnot přihlašovacích údajů klienta  
 Na straně klienta, nastavte pomocí hodnot přihlašovacích údajů klienta <xref:System.ServiceModel.Description.ClientCredentials> třídy a vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy. Následující kód nastaví certifikát jako přihlašovací údaje pro klienta pomocí protokolu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
