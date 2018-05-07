---
title: Programování zabezpečení WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3eb645dcc5b8cc1c52818e290699ebadcd0943c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="programming-wcf-security"></a>Programování zabezpečení WCF
Toto téma popisuje základní programovací úlohy použité k vytvoření zabezpečené aplikace Windows Communication Foundation (WCF). Toto téma popisuje pouze ověřování, důvěrnost a integritu, souhrnně označované jako *přenosu zabezpečení*. Toto téma nepopisuje autorizace (řízení přístupu k prostředkům nebo službám); informace o ověřování najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Cenné Úvod k koncepty zabezpečení, zejména pokud jde o WCF, najdete na webu MSDN na sadu vzory a postupy kurzy [scénáře, vzory a implementace pokyny pro webové služby vylepšení (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programování zabezpečení WCF je založen na nastavení následující tři kroky: režim zabezpečení, typu pověření klienta a hodnot přihlašovacích údajů. Abyste mohli provést tyto kroky buď prostřednictvím kódu nebo konfigurace.  
  
## <a name="setting-the-security-mode"></a>Nastavení režimu zabezpečení  
 Následující části jsou vysvětleny obecné kroky pro programování s režimem zabezpečení ve WCF:  
  
1.  Vyberte jeden z předdefinovaných vazby, které jsou vhodné pro vaše požadavky aplikací. Seznam voleb vazby najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md). Téměř každý vazby má ve výchozím nastavení zabezpečení povoleno. Jedinou výjimkou je <xref:System.ServiceModel.BasicHttpBinding> – třída (pomocí konfigurace, [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Vazba, kterou vyberete určuje přenosu. Například <xref:System.ServiceModel.WSHttpBinding> používá protokol HTTP jako přenos; <xref:System.ServiceModel.NetTcpBinding> používá protokol TCP.  
  
2.  Vyberte jeden z režimů zabezpečení pro vazbu. Všimněte si, že vazby, kterou vyberete, určuje možnosti k dispozici režimu. Například <xref:System.ServiceModel.WSDualHttpBinding> neumožňuje zabezpečení přenosu (není možnost). Podobně ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umožňuje zabezpečení zpráv.  
  
     Máte tři možnosti:  
  
    1.  `Transport`  
  
         Zabezpečení přenosu závisí na mechanismu, který používá vazby, které jste vybrali. Například, pokud používáte `WSHttpBinding` je mechanismus zabezpečení Secure Sockets Layer (SSL) (také mechanismus pro protokol HTTPS). Hlavní výhodou zabezpečení přenosu je obecně řečeno, zajišťuje dobrý propustnost, bez ohledu na to, které přenosu používáte. Však obsahuje dvě omezení: první je, že přenosový mechanismus Určuje typ pověření pro ověření uživatele. Toto je nevýhodou pouze v případě, že služba potřebuje pro spolupráci s jinými službami, které potřebují různé typy přihlašovacích údajů. Druhá je, že, protože zabezpečení není použita na úrovni zpráv, zabezpečení je implementovaná v segmentu směrování způsobem spíše než začátku do konce. Toto omezení druhé je problém pouze v případě, že cesta zpráv mezi klientem a službou obsahuje prostředníci. Další informace o které přenosu použít, najdete v části [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Další informace o používání zabezpečení přenosu najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         Zabezpečení zpráv znamená, že každá zpráva obsahuje potřebné hlavičky a zabezpečení dat, které chcete zachovat zprávy. Vzhledem k tomu, že se liší složení záhlaví může obsahovat libovolný počet přihlašovací údaje. Faktor to stane, pokud jste se spolupráce s jinými službami této poptávky typ určité pověření, který nelze zadat přenosový mechanismus, nebo pokud zprávy musí být použit s více než jedna služba, kde každá služba vyžaduje typ různých přihlašovacích údajů.  
  
         Další informace najdete v tématu [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Tato volba používá přenosové vrstvy zabezpečit přenos zpráv, při každé zprávy je i bohaté přihlašovací údaje potřebovat další služby. Kombinuje výkon výhod zabezpečení přenosu s výhodou bohaté pověření zabezpečení zpráv. Toto je k dispozici následující vazby: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, a <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Pokud se rozhodnete použít zabezpečení přenosu pro protokol HTTP (jinými slovy, HTTPS), musíte také nakonfigurovat certifikát SSL hostitele a povolit protokol SSL na portu. Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Pokud používáte <xref:System.ServiceModel.WSHttpBinding> a není potřeba navázat zabezpečené relaci, nastavte <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost `false`.  
  
     Zabezpečené relace nastane, když klient a služba vytvoření kanálu pomocí symetrického klíče (klient i server používají stejný klíč délky konverzace, dokud nezavřete dialogové okno).  
  
## <a name="setting-the-client-credential-type"></a>Nastavení typu pověření klienta  
 Vyberte typ pověření klienta podle potřeby. Další informace najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). K dispozici jsou následující typy pověření klienta:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 V závislosti na tom, jak nastavit režim musíte nastavit typ přihlašovacích údajů. Například pokud jste vybrali `wsHttpBinding`a nastavili režim "Zpráva,", pak můžete také nastavit `clientCredentialType` atribut elementu zprávy na jednu z následujících hodnot: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
 Jakmile vyberete typu pověření klienta, je nutné nastavit skutečné přihlašovací údaje pro službu a klienta pro použití. Ve službě, jsou přihlašovací údaje nastavit pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy a vrácený <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost <xref:System.ServiceModel.ServiceHostBase> – třída. Vazba používá znamená typ přihlašovacích údajů služby, vybrali režim zabezpečení a typ pověření klienta. Následující kód nastaví certifikát pro přihlašovací údaje služby.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Nastavení hodnot přihlašovacích údajů klienta  
 Na straně klienta, nastavte hodnoty přihlašovacích údajů klienta pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy a vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> – třída. Následující kód nastaví certifikát jako pověření klienta pomocí protokolu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
