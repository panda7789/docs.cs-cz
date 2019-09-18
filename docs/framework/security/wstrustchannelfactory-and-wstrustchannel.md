---
title: WSTrustChannelFactory a WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: e00f3ae25a50c2fb3f34f4c04d02cde574b3da17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044919"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory a WSTrustChannel
Pokud už jste obeznámeni se službou Windows Communication Foundation (WCF), víte, že klient WCF už ve federaci ví. Konfigurací klienta WCF pomocí <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobné vlastní vazby můžete povolit federované ověřování pro službu.

 Služba WCF získá token vydaný službou tokenu zabezpečení (STS) na pozadí a pomocí tohoto tokenu ověří službu. Hlavním omezením tohoto přístupu je, že neexistuje žádná viditelnost komunikace klienta se serverem. Služba WCF automaticky vygeneruje token zabezpečení Request (RST) na službu STS na základě parametrů vydaných tokenů ve vazbě. To znamená, že klient nemůže měnit parametry RST na žádost, zkontrolovat odpověď tokenu zabezpečení (RSTR) žádosti o získání informací, jako jsou například deklarace identity zobrazení, nebo uložit token do mezipaměti pro budoucí použití.

 V současné době je klient služby WCF vhodný pro scénáře základní federace. Jeden z hlavních scénářů, které podporuje technologie Windows Identity Foundation (WIF), ale vyžaduje kontrolu nad RST na úrovni, kterou WCF snadno nepovoluje. Proto WIF přidá funkce, které vám poskytnou větší kontrolu nad komunikací s STS.

 WIF podporuje následující scénáře federace:

- Použití klienta WCF bez závislostí WIF k ověření pro federované služby

- Povolení WIF v klientovi WCF pro vložení elementu ActAs nebo OnBehalfOf do pole RST do služby STS

- Použití samotného WIF k získání tokenu ze služby STS a následnému povolení ověřování klienta WCF s tímto tokenem. Další informace najdete v tématu [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) Sample.

 První scénář je samozřejmý: Stávající klienti WCF budou dál spolupracovat s předávajícími stranami WIF a STS. Toto téma pojednává o zbývajících dvou scénářích.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Vylepšení stávajícího klienta WCF pomocí ActAs/OnBehalfOf
V typickém scénáři delegování identity klient volá službu střední vrstvy, která pak zavolá back-end službu. Služba střední vrstvy funguje jako klient nástroje nebo funguje jako jeho jménem.

> [!TIP]
> Jaký je rozdíl mezi ActAs a OnBehalfOf?
>
> Z hlediska protokolu WS-Trust:
>
> 1. Element ActAs RST indikuje, že žadatel chce token, který obsahuje deklarace identity o dvou různých entitách: žadateli a externí entitu reprezentovanou tokenem v elementu ActAs.
> 2. Element OnBehalfOf RST indikuje, že žadatel chce token, který obsahuje deklarace identity jenom o jedné entitě: Externí entita reprezentovaná tokenem v elementu OnBehalfOf.
>
> Funkce ActAs se obvykle používá ve scénářích, které vyžadují složené delegování, přičemž konečný příjemce vydaného tokenu může zkontrolovat celý řetěz delegování a zobrazit nejenom klienta, ale všechny zprostředkovatele. To umožňuje provádět řízení přístupu, auditování a další související aktivity na základě celého řetězce delegování identity. Funkce ActAs se běžně používá v vícevrstvých systémech k ověřování a předávání informací o identitách mezi vrstvami bez nutnosti předat tyto informace na vrstvě Application/Business Logic.
>
> Funkce OnBehalfOf se používá ve scénářích, kdy je důležitá pouze identita původního klienta a je v podstatě stejná jako funkce zosobnění identity, která je v systému Windows k dispozici. Při použití OnBehalfOf může konečný příjemce vydaného tokenu zobrazit jenom deklarace identity o původním klientovi a informace o prostředníkech se nezachovají. Jedním z běžných vzorů, ve kterých se používá funkce OnBehalfOf, je vzor proxy serveru, kde klient nemůže získat přístup k STS přímo, ale komunikuje prostřednictvím brány proxy serveru. Brána proxy ověří volajícího a vloží informace o volajícím do prvku OnBehalfOf zprávy RST, kterou pak pošle skutečné službě STS ke zpracování. Výsledný token obsahuje jenom deklarace, které souvisejí s klientem proxy serveru, takže proxy serveru je zcela transparentní na přijímači vydaného tokenu. Všimněte si, že WIF nepodporuje \<wsse: SecurityTokenReference > ani \<wsa: EndpointReferences \<> jako podřízenou položku wst: OnBehalfOf >. Specifikace WS-Trust umožňuje třem způsobům identifikace původního žadatele (jménem uživatele, který funguje). Toto jsou:
>
> - Odkaz na token zabezpečení Odkaz na token, buď ve zprávě, nebo může být načten mimo pásmo).
> - Odkaz na koncový bod Používá se jako klíč pro vyhledávání dat, opět mimo pásmo.
> - Token zabezpečení Přímo identifikuje původního žadatele.
>
> WIF podporuje pouze tokeny zabezpečení, které jsou šifrované nebo nešifrované, jako přímý podřízený prvek \<wst: OnBehalfOf >.

 Tyto informace jsou předány vydavateli WS-Trust pomocí prvků tokenu ActAs a OnBehalfOf v RST.

 WCF zpřístupňuje bod rozšiřitelnosti pro vazbu, která umožňuje přidat libovolné elementy XML do RST. Vzhledem k tomu, že bod rozšiřitelnosti je svázán s vazbou, musí být scénáře, které vyžadují obsah RST v závislosti na volání, znovu vytvořit klienta pro každé volání, což snižuje výkon. WIF používá metody `ChannelFactory` rozšíření třídy, aby umožnila vývojářům připojit jakýkoliv token, který se získá mimo pásmo, do RST. Následující příklad kódu ukazuje, jak převzít token, který představuje klienta (například token X. 509, username nebo Security Assertion Markup Language (SAML) a připojí ho k RST, která je odeslána vystaviteli.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WIF poskytuje následující výhody:

- Možnost RST se dá upravit na kanál; Proto služby střední vrstvy nemusí znovu vytvářet továrny kanálů pro každého klienta, což zvyšuje výkon.

- Tato funkce funguje se stávajícími klienty WCF, což usnadňuje cestu k snadnému upgradu pro existující služby střední vrstvy WCF, které chtějí povolit sémantiku delegování identity.

 Stále ale neexistuje žádná viditelnost komunikace klienta se službou STS. Podíváme se do třetího scénáře.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Komunikace přímo s vystavitelem a používání vydaného tokenu k ověření
V některých pokročilých scénářích není rozšíření klienta služby WCF dostatečné. Vývojáři, kteří používají pouze WCF, obvykle používají zprávy ve smlouvách/zprávách odchozích zpráv a zpracovávají odpovědi vystavitelů na straně klienta ručně.

WIF zavádí <xref:System.ServiceModel.Security.WSTrustChannelFactory> třídy a <xref:System.ServiceModel.Security.WSTrustChannel> , aby klient mohl komunikovat přímo s vystavitelem WS-Trust. Třídy <xref:System.ServiceModel.Security.WSTrustChannelFactory> a<xref:System.ServiceModel.Security.WSTrustChannel> umožňují tok silně typovaného typu RST a RSTR objektů do toku mezi klientem a vystavitelem, jak je znázorněno v následujícím příkladu kódu.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

Všimněte si, `out` že parametr <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> v metodě umožňuje přístup k RSTR pro kontrolu na straně klienta.

Zatím jste viděli jenom, jak získat token. Token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel> objektu, `GenericXmlSecurityToken` je, který obsahuje všechny informace, které jsou nezbytné pro ověřování předávající strany. Následující příklad kódu ukazuje, jak použít tento token.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

Metoda <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> rozšíření `ChannelFactory` na objektu indikuje WIF, že jste token získali mimo pásmo, a že by měl zastavit normální volání WCF do vystavitele a místo toho použít token, který jste získali k ověřování předávající strany. To má následující výhody:

- Poskytuje plnou kontrolu nad procesem vystavení tokenu.

- Podporuje scénáře ActAs/OnBehalfOf, a to přímo nastavením těchto vlastností v odchozím parametru RST.

- Umožňuje dynamické rozhodování o důvěryhodnosti na straně klienta na základě obsahu RSTR.

- Umožňuje ukládat do mezipaměti a znovu použít token, který je vrácen z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory>a <xref:System.ServiceModel.Security.WSTrustChannel> umožňují kontrolu mezipamětí kanálu, selhání a sémantiky obnovení v souladu s osvědčenými postupy WCF.

## <a name="see-also"></a>Viz také:

- [Funkce technologie WIF](wif-features.md)
