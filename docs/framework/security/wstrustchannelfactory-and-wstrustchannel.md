---
title: WSTrustChannelFactory a WSTrustChannel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 35f4449f7a826ea49be750cd750cb989c8c455fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory a WSTrustChannel
Pokud jste již obeznámeni s Windows Communication Foundation (WCF), víte, že klienta WCF již federační vědět. Podle konfigurace klienta WCF s <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobné vlastní vazby, můžete povolit federovaného ověřování do služby.  
  
 WCF získá token, který je vydaný služby tokenů zabezpečení (STS) na pozadí a používá tento token k ověření služby. Hlavní omezení tohoto přístupu je, že neexistuje žádná přehled komunikaci klienta se serverem. WCF automaticky generuje token zabezpečení požadavku (RVNÍ) na službu STS založenou na parametrech vydaných tokenů na vazby. To znamená, že klienta nelze měnit parametry RVNÍ každý požadavek, zkontrolujte odpovědi tokenu zabezpečení požadavku (RSTR) Chcete-li získat informace, jako jsou deklarace identity zobrazení nebo mezipaměti token pro budoucí použití.  
  
 V současné době je vhodná pro scénáře základní federační klienta WCF. Mezi hlavní scénáře, které podporuje Windows Identity Foundation (WIF) ale vyžaduje kontrolu nad RVNÍ na úrovni, který WCF neumožňuje snadno. Proto WIF přidá funkce, které získáte větší kontrolu nad komunikace s Služba tokenů zabezpečení.  
  
 WIF podporuje následující scénáře federation:  
  
-   Pomocí klienta WCF bez závislostí WIF k ověření federované služby  
  
-   Povolit WIF na klienta WCF vložení element ActAs nebo OnBehalfOf do RVNÍ na službu STS  
  
-   Použití WIF samostatně k získání tokenu z Služba tokenů zabezpečení a pak povolte klienta WCF k ověřování pro tento token. Další informace najdete v tématu [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) ukázka.  
  
 První scénář je není potřeba vysvětlovat: Klienti existující WCF bude pokračovat v práci s WIF předávající strany a STSs. Toto téma popisuje zbývající dva scénáře.  
  
## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Rozšíření stávajícího klienta WCF s ActAs / OnBehalfOf  
 Ve scénáři delegování typické identity klienta volá střední vrstvy služby, která pak zavolá back-end službu. Služba střední vrstvy funguje jako nebo funguje jménem klienta.  
  
> [!TIP]
>  Jaký je rozdíl mezi ActAs a OnBehalfOf?  
>   
>  Z hlediska získáváním WS-Trust:  
>   
>  1.  Element ActAs RVNÍ označuje, že žadatel chce token, který obsahuje deklarace identity o dvou různých entit: žadatel a externí entity reprezentována v elementu ActAs token.  
> 2.  Element OnBehalfOf RVNÍ označuje, že žadatel chce token, který obsahuje pouze jednu entitu deklarací identity: externí entitu reprezentovanou objektem token v elementu OnBehalfOf.  
>   
>  Funkci ActAs se obvykle používá ve scénářích, které vyžadují složené delegování, kde můžete konečné příjemce vydaných tokenu zkontrolujte řetězu celý delegování a najdete v části nejen klienta, ale všichni zprostředkovatelé. To umožňuje, aby ji provést řízení přístupu, auditování a další související aktivity podle řetězu delegování celý identity. Funkci ActAs je běžně používaných v systémech víceúrovňových k ověření a předání informací o identitách mezi vrstvami bez nutnosti předejte tyto informace ve vrstvě aplikace nebo obchodní logiku.  
>   
>  Funkce OnBehalfOf se používá ve scénářích, kde je důležité pouze identitu původního klienta a je efektivně stejná jako identity zosobnění funkce dostupné v systému Windows. Když OnBehalfOf se používá, konečné příjemce vydaných tokenu uvidí jenom deklarace identity o původní klienta a informace o prostředníci není zachován. Jednou z běžných vzor, kde se používá funkci OnBehalfOf je vzor proxy serveru, kde klient nemůže získat službu STS přímo, ale místo toho komunikuje prostřednictvím proxy serveru brány. Proxy server brány ověří volajícího a vloží informace o volajícím do elementu OnBehalfOf RVNÍ zprávy, které pak odešle skutečné služby tokenů zabezpečení pro zpracování. Výsledný token obsahuje jenom deklarace identity související se proxy serveru, provedení zcela transparentní proxy serveru k příjemce vydaných tokenu. Všimněte si, že WIF nepodporuje \<wsse: SecurityTokenReference > nebo \<wsa:EndpointReferences > jako podřízený \<wst:OnBehalfOf >. Specifikace WS-Trust umožňuje tři způsoby, jak identifikovat původnímu žadateli (jménem kterého je funguje proxy serveru). Jsou to:  
>   
>  -   Informace o tokenu zabezpečení. Odkaz na token, buď ve zprávě, nebo může být načtena z vzdálené).  
> -   Odkaz na koncový bod. Použít jako klíč pro vyhledávání dat, opět vzdáleně.  
> -   Token zabezpečení. Identifikuje původní žadatele přímo.  
>   
>  WIF podporuje tokeny pouze zabezpečení, šifrován nebo bez šifrování, jako přímý podřízeného prvku \<wst:OnBehalfOf >.  
  
 Tyto informace předávají v tokenu elementy ActAs a OnBehalfOf RVNÍ WS-Trust Issuer.  
  
 WCF zpřístupní bod rozšiřitelnosti na vazba, která umožňuje libovolné elementů XML pro přidání do RVNÍ. Ale vzhledem k tomu, že bod rozšiřitelnosti je vázaný na vazby, scénáře, které vyžadují obsah RVNÍ k odlišení za volání nutné znovu vytvořit klienta pro každé volání, takže se sníží výkon. WIF používá rozšiřující metody na `ChannelFactory` třídu, která umožňuje vývojářům připojit žádné token, který je získat vzdálenou správu na RVNÍ. Následující příklad kódu ukazuje, jak provést token, který představuje klienta (například X.509, uživatelské jméno nebo token zabezpečení kontrolního výrazu SAML (Markup Language)) a připojte ji k RVNÍ, které je odesláno vystavitele.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello("Hi!");  
```  
  
 WIF poskytuje následující výhody:  
  
-   RVNÍ můžete změnit na kanál; střední vrstvy služby nemusí proto se znovu vytvořit vytváření kanálů pro každého klienta, což zvyšuje výkon.  
  
-   Tento postup funguje s existující klienti WCF, který umožňuje snadnou cestu upgradu pro stávající střední vrstvy služby WCF, které chcete povolit sémantiku delegování identity.  
  
 Je však stále žádné Přehled komunikace klienta s Služba tokenů zabezpečení. Podíváme to v třetí scénář.  
  
## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Komunikovat přímo s vystavitele a k ověření pomocí vydaných tokenu  
 Pro některé pokročilé scénáře rozšíření klienta WCF nestačí. Vývojáři, kteří používají pouze WCF obvykle používat zprávy v / zpráva se měnící a zpracování na straně klienta analýze odpovědi vystavitele ručně.  
  
 Zavádí WIF <xref:System.ServiceModel.Security.WSTrustChannelFactory> a <xref:System.ServiceModel.Security.WSTrustChannel> třídy umožníte klient komunikovat přímo s WS-Trust vystavitele. <xref:System.ServiceModel.Security.WSTrustChannelFactory> a <xref:System.ServiceModel.Security.WSTrustChannel> třídy povolit RVNÍ a RSTR objektů se silným typem tok mezi klientem a vystavitele, jak je znázorněno v následujícím příkladu kódu.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Všimněte si, že `out` parametr na <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metoda umožňuje přístup k RSTR kontroly na straně klienta.  
  
 Zatím jste pouze viděli jak získat token. Token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel> objekt `GenericXmlSecurityToken` obsahující všechny informace, které jsou nezbytné pro ověřování k předávající straně. Následující příklad kódu ukazuje, jak používat tento token.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello("Hi!");  
```  
  
 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Rozšiřující metody na `ChannelFactory` objektu určuje WIF, který jste získali token vzdálené správy a měl by zastavit normální WCF volání vystavitele a místo toho použít token, který jste získali k ověření předávající straně. To má tyto výhody:  
  
-   Nabízí úplnou kontrolu nad tímto procesem vystavování tokenů.  
  
-   Podporuje ActAs / OnBehalfOf scénáře pomocí přímo odchozí RVNÍ nastavení těchto vlastností.  
  
-   Umožňuje dynamické klienta vztahu důvěryhodnosti z RSTR obsahu na základě rozhodnutí, která má být provedeno.  
  
-   Umožňuje ukládat do mezipaměti a opakovaně používat token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metoda.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory>a <xref:System.ServiceModel.Security.WSTrustChannel> povolit pro řízení kanál ukládání do mezipaměti, selhání a obnovení sémantiku podle doporučených postupů WCF.  
  
## <a name="see-also"></a>Viz také  
 [Funkce technologie WIF](../../../docs/framework/security/wif-features.md)
