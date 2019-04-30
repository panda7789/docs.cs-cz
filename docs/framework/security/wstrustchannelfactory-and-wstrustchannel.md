---
title: WSTrustChannelFactory a WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: ecc62292b2b064219127c369f43141a31ffe606d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780065"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory a WSTrustChannel
Pokud jste už obeznámení s Windows Communication Foundation (WCF), víte, že klient WCF je již federace vědět. Pomocí konfigurace klienta WCF s <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobné vlastní vazby, můžete povolit federované ověřování do služby.

 WCF získá token, který je vydaný služby tokenů zabezpečení (STS) na pozadí a použije tento token k ověření ve službě. Hlavní omezení tohoto přístupu je, že neexistuje žádná přehled o komunikaci klienta se serverem. WCF automaticky generuje token zabezpečení požadavku (RVNÍ) na službu STS, na základě vydaný token parametrů ve vazbě. To znamená, že klient nemůže se liší parametry RVNÍ každý požadavek, zkontrolovat odpovědi tokenu zabezpečení požadavku (RSTR) Chcete-li získat informace, jako je zobrazení deklarací identity, mezipaměti token pro budoucí použití.

 V současné době je vhodný pro základní federacích klienta WCF. Jedním z hlavních scénářů, které podporuje technologie Windows Identity Foundation (WIF) ale vyžaduje kontrolu nad RVNÍ na úrovni, která není povolena snadno WCF. Technologie WIF proto přidá funkce, které poskytují větší kontrolu nad komunikace se službou tokenů zabezpečení.

 Technologie WIF podporuje následující scénáře federace:

- Pomocí klienta WCF nezávisle technologie WIF za účelem ověření k federované službě

- Povolení technologie WIF na klienta WCF na vkládání elementů ActAs nebo OnBehalfOf do RVNÍ na službu STS

- Pomocí technologie WIF samostatně, aby získat token od služby STS a pak povolte klienta WCF na ověření pomocí tohoto tokenu. Další informace najdete v tématu [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) vzorku.

 První scénář je zřejmých: Existující klienti WCF budou nadále fungovat s přijímajících stran, které technologie WIF a služby tokenů zabezpečení. Toto téma popisuje zbývající dva scénáře.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Vylepšení stávajícího klienta WCF s ActAs nebo OnBehalfOf
V případě delegování identity typické klient volá střední vrstvy služby, která potom volá back-end služby. Služba střední vrstvy funguje jako, nebo funguje jménem klienta.

> [!TIP]
> Jaký je rozdíl mezi ActAs a prostřednictvím profilu OnBehalfOf?
>
> Z hlediska protokolu WS-Trust:
>
> 1. Element ActAs RVNÍ označuje, žadatel vyžaduje token, který obsahuje deklarace identity o dvou různých entit: žadatel a externí entitu reprezentovanou objektem token v elementu ActAs.
> 2. Element prostřednictvím profilu OnBehalfOf RVNÍ označuje, že žadatel vyžaduje token, který obsahuje pouze jednu entitu deklarace identity: externí entitu reprezentovanou objektem token v elementu prostřednictvím profilu OnBehalfOf.
>
> Funkce ActAs se obvykle používá ve scénářích, které vyžadují složené delegování, kde kontrolovat celou delegování řetězce a vidět nejen klienta, ale všichni zprostředkovatelé konečného příjemce vydaný token. To umožňuje provádět řízení přístupu, auditování a další související aktivity založené na řetězci delegování celý identity. ActAs funkce se běžně používá v systémech vícevrstevných k ověření a předání informací o identitách mezi vrstvami, aniž byste museli předejte tyto informace ve vrstvě aplikace a obchodní logiku.
>
> Prostřednictvím profilu OnBehalfOf funkce se používá v situacích, kdy pouze identitu původního klienta je důležité a je v podstatě totéž jako identita zosobnění funkci k dispozici ve Windows. Při použití prostřednictvím profilu OnBehalfOf konečného příjemce vydaný token uvidí jenom deklarace identity o původní klienta a informace o zprostředkovateli nezachová. Ten, který je běžný vzor, kde se používá funkci prostřednictvím profilu OnBehalfOf vzor proxy serveru, kde klient nemůže získat Služba tokenů zabezpečení přímo, ale místo toho komunikuje přes proxy server brány. Proxy server brány ověří volajícího a vloží informace o volajícím do elementu prostřednictvím profilu OnBehalfOf RVNÍ zpráva, která pak odešle do skutečných STS pro zpracování. Výsledný token obsahuje pouze nároky týkající se klienta proxy, aby zcela transparentní proxy server příjemci vydaný token. Všimněte si, že technologie WIF nepodporuje \<wsse: SecurityTokenReference > nebo \<wsa:EndpointReferences > jako podřízený objekt \<wst:OnBehalfOf >. Specifikace WS-Trust umožňuje tři způsoby, jak identifikovat ho původnímu žadateli (jménem kterého se chová proxy serveru). Toto jsou:
>
> - Odkaz na token zabezpečení. Odkaz na token, buď ve zprávě, nebo může být načtena z obsluhy vzdálené správy).
> - Reference koncového bodu. Chcete-li vyhledat data opět vzdáleně použít jako klíč.
> - Token zabezpečení. Identifikuje původní žadatel přímo.
>
> Technologie WIF podporuje pouze zabezpečení tokeny, šifrované a nešifrované jako přímý podřízený prvek \<wst:OnBehalfOf >.

 Tyto informace předávají do vystavitele WS-Trust ActAs a prostřednictvím profilu OnBehalfOf token prvky v RVNÍ.

 WCF zpřístupní bod rozšiřitelnosti pro vazbu, která umožňuje libovolnými prvky XML mají být přidány do RVNÍ. Ale protože bodu rozšiřitelnosti se váže na vazby, scénáře, které vyžadují obsah RVNÍ se liší podle volání musí znovu vytvořit klienta pro všechna volání, což snižuje výkon. Technologie WIF používají rozšiřující metody na `ChannelFactory` třídu, která umožňuje vývojářům připojit žádný token, která se získá mimo pásmo RVNÍ. Následující příklad kódu ukazuje, jak provést token, který představuje klienta (například X.509, uživatelské jméno nebo token zabezpečení kontrolního výrazu SAML (Markup Language)) a připojit ho k RVNÍ, které je odesláno vystavitele.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 Technologie WIF nabízí následující výhody:

- Je možné upravit RVNÍ jeden kanál; střední vrstvy služby, proto není potřeba znovu vytvořit objekt pro vytváření kanálů pro každého klienta, což zvyšuje výkon.

- Tento postup funguje s existující klienti WCF, která umožňuje snadný způsob upgradu pro existující střední vrstvy služby WCF, které chcete povolit sémantiku delegování identity.

 Existuje ale stále žádné přehled o komunikaci klienta pomocí služby STS. Prozkoumáme to v třetí scénář.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Komunikuje přímo s vystavitele a pomocí vydaný Token pro ověření
Pro některé pokročilé scénáře vylepšení klienta WCF nestačí. Vývojáři, kteří používají obvykle pouze WCF používat zprávy v / zprávy smlouvy a zpracování na straně klienta ruční parsování odpovědi vystavitele.

Zavádí technologie WIF <xref:System.ServiceModel.Security.WSTrustChannelFactory> a <xref:System.ServiceModel.Security.WSTrustChannel> třídy, které umožní klient komunikovat přímo s vystavitele WS-Trust. <xref:System.ServiceModel.Security.WSTrustChannelFactory> a <xref:System.ServiceModel.Security.WSTrustChannel> třídy povolit RVNÍ a RSTR objektů se silným typem tok mezi klientem a vystavitele, jak je znázorněno v následujícím příkladu kódu.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

Všimněte si, že `out` parametru u <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metoda umožňuje přístup k RSTR pro kontroly na straně klienta.

Zatím jste pouze seznámili s postupem k získání tokenu. Token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel> je objekt `GenericXmlSecurityToken` , která obsahuje všechny informace, které jsou nezbytné pro ověřování a předávající stranou. Následující příklad kódu ukazuje, jak používat tento token.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

<xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Rozšiřující metody na `ChannelFactory` objekt znamená technologie WIF, který jste získali token mimo IP síť a měl by zastavit normální volání WCF vystavitele a místo toho použijte token, který jste získali k ověření předávající straně. To má tyto výhody:

- Poskytuje plnou kontrolu nad procesu vystavování tokenů.

- Podporuje ActAs nebo OnBehalfOf scénáře podle přímo na odchozí RVNÍ nastavení těchto vlastností.

- Umožňuje dynamického vztahu důvěryhodnosti na straně klienta na základě rozhodnutí o obsahu RSTR.

- To umožňuje ukládat do mezipaměti a opakovaně používat token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory> a <xref:System.ServiceModel.Security.WSTrustChannel> povolit pro ovládací prvek kanál sémantiky ukládání do mezipaměti, selhání a obnovení podle osvědčených postupů WCF.

## <a name="see-also"></a>Viz také:

- [Funkce technologie WIF](../../../docs/framework/security/wif-features.md)