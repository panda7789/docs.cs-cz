---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 57a1513f6de7f7bd9ea441b6cbc3db6a06d76fc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940265"
---
# <a name="wsfederation"></a>\<wsFederation>
Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<system.identityModel.services>  
\<federationConfiguration>  
\<wsFederation>  
  
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
|authenticationType|Identifikátor URI, který určuje typ ověřování. Nastaví parametr wauth žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není obsažen parametr wauth.|  
|aktuálnosti|Požadovaný maximální věk žádostí o ověření v řádu minut. Nastaví parametr wfresh žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je nula. Volitelný parametr. **Upozornění**  V příští verzi .NET Framework 4,5 `freshness` bude atribut typu `xs:string` a `null`jeho výchozí hodnota bude.|  
|homeRealm|Domovská sféra poskytovatele identity (IdP), která se má použít pro ověřování. Nastaví parametr pro žádost o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že parametr Wh není v požadavku zahrnut.|  
|issuer|Identifikátor URI zamýšleného vystavitele tokenu Nastaví základní adresu URL žádostí o přihlášení WS-Federation a požadovaných žádostí o odhlášení.|  
|persistentCookiesOnPassiveRedirects|Určuje, zda jsou při ověřování vydány trvalé soubory cookie. Volitelný parametr. Výchozí hodnota je "false", soubory cookie nejsou vydány.|  
|passiveRedirectEnabled|Určuje, jestli je povolený WSFAM k automatickému přesměrování neautorizovaných požadavků na STS. Volitelný parametr. Výchozí hodnota je "true", automaticky se přesměrují neoprávněné požadavky.|  
|politických|Adresa URL, která určuje umístění příslušné zásady, která se má použít při žádostech o přihlášení. Výchozí hodnota je prázdný řetězec. Nastaví parametr wp pro žádost o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wp není v požadavku zahrnut.|  
|sféry|Identifikátor URI žádající sféry. (Identifikátor URI, který identifikuje předávající stranu (RP) na službu tokenů zabezpečení (STS).) Nastaví parametr žádosti o přihlášení k wtrealm protokolu WS-Federation. Povinný parametr.|  
|zpáteční|Adresa URL, která určuje adresu, na které má aplikace předávající strany (RP) přijímat odpovědi ze služby tokenu zabezpečení (STS). Nastaví parametr wreply žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není obsažen parametr wreply.|  
|request|Požadavek na vystavení tokenu Nastaví parametr wreq žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není obsažen Parametr wreq. Nezahrnuje-li parametr wreq ani parametr wreqptr v požadavku, znamená to, že služba STS ví, jaký typ tokenu je vydávat.|  
|requestPtr|Adresa URL, která určuje umístění žádosti o vystavení tokenu. Nastaví parametr wreqptr žádosti. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není obsažen parametr wreqptr. Nezahrnuje-li parametr wreq ani parametr wreqptr v požadavku, znamená to, že služba STS ví, jaký typ tokenu je vydávat.|  
|Atribut|Určuje, jestli musí komunikace se službou tokenu zabezpečení (STS) používat protokol HTTPS. Volitelný parametr. Výchozí hodnota je "true", je nutné použít HTTPS.|  
|prostředek|Identifikátor URI, který identifikuje přistupující prostředek, předávající straně (RP) na službu tokenů zabezpečení (STS). Volitelný parametr. Nastaví parametr wres žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není obsažen parametr wres. **Poznámka:** wres je starší parametr. Místo toho zadejte atribut pro použití parametru wtrealm. `realm`|  
|signInQueryString|Poskytuje bod rozšiřitelnosti pro určení parametrů dotazu definovaných aplikací v adrese URL požadavku na přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry. Parametry jsou zadány jako fragment řetězce dotazu pomocí následujícího tvaru: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru je třeba zadat znak "&" v řetězci dotazu pomocí odkazu na `&`entitu.|  
|signOutQueryString|Poskytuje bod rozšiřitelnosti pro určení parametrů dotazu definovaných aplikací v adrese URL požadavku na přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry. Parametry jsou zadány jako fragment řetězce dotazu pomocí následujícího tvaru: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru je třeba zadat znak "&" v řetězci dotazu pomocí odkazu na `&`entitu.|  
|signOutReply|Určuje adresu URL, na kterou by měl klient během pasivního odhlašování prostřednictvím protokolu WS-Federation přesměrovat službu tokenů zabezpečení (STS). Nastaví parametr wreply u žádosti o přihlášení ke službě WS-Federation. Volitelný parametr. Výchozí hodnota je prázdný řetězec, který určuje, že do požadavku by neměly být zahrnuty žádné další parametry.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Obsahuje nastavení, která konfigurují <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> a (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `<wsFederation>` elementu můžete nakonfigurovat výchozí nastavení parametrů WS-Federation a výchozí chování pro WSFAM. Nastavení parametru WS-Federation definované v rámci `<wsFederation>` nastavených ekvivalentních vlastností, které <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> jsou vystavené třídou Tyto vlastnosti zůstávají u všech požadavků vydaných WSFAM stejné. Parametry WS-Federation můžete změnit dynamicky během zpracování žádosti přidáním obslužných rutin událostí pro události vystavené službou WSFAM; například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událost. Další informace naleznete v dokumentaci pro <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídu.  
  
 Element je reprezentován <xref:System.IdentityModel.Services.Configuration.WSFederationElement>třídou. `<wsFederation>` Samotný objekt konfigurace je reprezentován <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> třídou. Jedna <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instance je nastavena <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> na objekt <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> , který je k dispozici prostřednictvím vlastnosti a poskytuje konfiguraci pro WSFAM.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje `<wsFederation>` prvek, který určuje nastavení pro WSFAM.  
  
> [!WARNING]
>  V tomto příkladu WSFAM není nutné používat protokol HTTPS. Důvodem je, že `requireHttps` atribut `<wsFederation>` prvku je nastaven `false`. Toto nastavení se nedoporučuje pro většinu produkčních prostředí, protože může představovat bezpečnostní riziko.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
