---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152460"
---
# <a name="wsfederation"></a>\<wsFederation>
Poskytuje konfiguraci <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> pro (WSFAM).  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|authenticationType|Identifikátor URI, který určuje typ ověřování. Nastaví parametr wauth požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí je prázdný řetězec, který určuje, že parametr wauth není zahrnut v požadavku.|  
|Čerstvost|Požadovaný maximální stáří požadavků na ověření v minutách. Nastaví parametr wfresh požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí hodnota je nula. Nepovinný parametr. **Upozornění:**  V další verzi rozhraní .NET Framework `freshness` 4.5 bude `xs:string` atribut typu a `null`jeho výchozí hodnota bude .|  
|homeRealm|Domovská sféra zprostředkovatele identity (IdP), který se má použít k ověřování. Nastaví parametr ws-federation požadavek na přihlášení whr. Nepovinný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že parametr whr není zahrnut v požadavku.|  
|issuer|Identifikátor URI zamýšleného vystavittele tokenu. Nastaví základní adresu URL požadavků na přihlášení WS-Federation a požadovaných požadavků na odhlášení.|  
|persistentCookiesOnPassiveRedirects|Určuje, zda jsou při ověřování vydány trvalé soubory cookie. Nepovinný parametr. Výchozí hodnota je "false", cookies nejsou vydávány.|  
|passiveRedirectEnabled|Určuje, zda je wsfam povoleno automaticky přesměrovat neoprávněné požadavky na službu STS. Nepovinný parametr. Výchozí hodnota je "true", neoprávněné požadavky jsou automaticky přesměrovány.|  
|policy|Adresa URL, která určuje umístění příslušných zásad, které mají být používány při požadavcích na přihlášení. Výchozí hodnota je prázdný řetězec. Nastaví parametr wp požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wp není zahrnut v požadavku.|  
|Sféry|Identifikátor URI žádající sféry. (Identifikátor URI, který identifikuje předávající stranu (RP) ke službě tokenů zabezpečení (STS).) Nastaví parametr požadavku wtrealm WS-Federation pro přihlášení. Povinná hodnota.|  
|Odpověď|Adresa URL, která identifikuje adresu, na které by aplikace předávající strany (RP) chtěla přijímat odpovědi ze služby TOKEN zabezpečení (STS). Nastaví parametr wreply pro přihlášení ws-Federation. Nepovinný parametr. Výchozí je prázdný řetězec, který určuje, že parametr wreply není zahrnut v požadavku.|  
|Požadavek|Požadavek na vystavení tokenu. Nastaví parametr wreq požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí je prázdný řetězec, který určuje, že parametr wreq není zahrnut v požadavku. Není zahrnutí wreq nebo wreqptr parametr v požadavku znamená, že STS ví, jaký druh tokenu vydat.|  
|requestPtr|Adresa URL, která určuje umístění požadavku na vystavení tokenu. Nastaví parametr request wreqptr. Nepovinný parametr. Výchozí je prázdný řetězec, který určuje, že parametr wreqptr není zahrnut v požadavku. Není zahrnutí wreq nebo wreqptr parametr v požadavku znamená, že STS ví, jaký druh tokenu vydat.|  
|requireHttps|Určuje, zda je třeba, aby komunikace se službou tokenů zabezpečení (STS) používala protokol HTTPS. Nepovinný parametr. Výchozí hodnota je "true", musí být použit protokol HTTPS.|  
|prostředek|Identifikátor URI, který identifikuje prostředek, ke kterému se přistupuje, předávající strana (RP), do služby tokenů zabezpečení (STS). Nepovinný parametr. Nastaví parametr wres požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí je prázdný řetězec, který určuje, že parametr wres není zahrnut v požadavku. **Poznámka:** wres je starší parametr. Zadejte `realm` atribut, který má místo toho použít parametr wtrealm.|  
|signInQueryString|Poskytuje bod rozšiřitelnosti k určení parametrů dotazu definovaných aplikací v adrese URL požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry. Parametry jsou určeny jako fragment řetězce dotazu pomocí následujícího formuláře: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru musí být znak & v `&`řetězci dotazu určen pomocí odkazu na entitu .|  
|signOutQueryString|Poskytuje bod rozšiřitelnosti k určení parametrů dotazu definovaných aplikací v adrese URL požadavku na přihlášení WS-Federation. Nepovinný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry. Parametry jsou určeny jako fragment řetězce dotazu pomocí následujícího formuláře: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru musí být znak & v `&`řetězci dotazu určen pomocí odkazu na entitu .|  
|signOutReply|Určuje adresu URL, na kterou má být klient během pasivního odhlašování prostřednictvím protokolu WS-Federation přesměrován službou tokenů zabezpečení (STS). Nastaví parametr wreply v požadavku na odhlášení WS-Federation. Nepovinný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurují (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 Prvek můžete `<wsFederation>` použít ke konfiguraci výchozího nastavení parametrů WS-Federation a výchozího chování pro wsfam. WS-Federation nastavení parametrů `<wsFederation>` definované v rámci element <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> set ekvivalentní vlastnosti vystavené třídy. Tyto vlastnosti zůstávají stejné pro každý požadavek vydaný WSFAM. Parametry WS-Federation můžete během zpracování požadavku dynamicky změnit přidáním obslužných rutin událostí pro události vystavené službou WSFAM. například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událost. Další informace naleznete v dokumentaci pro třídu. <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
  
 Prvek `<wsFederation>` je reprezentován <xref:System.IdentityModel.Services.Configuration.WSFederationElement> třídou. Samotný objekt konfigurace je <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> reprezentován třídou. Jedna <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instance je nastavena na objekt, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> který je přístupný prostřednictvím vlastnosti a poskytuje konfiguraci pro WSFAM.  
  
## <a name="example"></a>Příklad  
 Následující jazyk XML `<wsFederation>` zobrazuje prvek, který určuje nastavení služby WSFAM.  
  
> [!WARNING]
> V tomto příkladu wsfam není nutné používat protokol HTTPS. Důvodem je, `requireHttps` že `<wsFederation>` atribut `false`na prvek je nastaven . Toto nastavení se nedoporučuje pro většinu produkčních prostředí, protože může představovat bezpečnostní riziko.  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
