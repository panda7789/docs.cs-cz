---
title: '&lt;wsFederation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e4779baa24e172affad2ed5e04451ad791d7cdf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
Obsahuje konfiguraci <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<system.identityModel.services >  
\<federationConfiguration >  
\<wsFederation >  
  
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
|authenticationType.|Identifikátor URI, který určuje typ ověřování. Nastaví parametr wauth WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wauth není zahrnutý v požadavku.|  
|aktuálnosti|Požadované maximální stáří požadavků na ověření v minutách. Nastaví parametr wfresh WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je nula. Volitelné. **Upozornění:** v další verzi rozhraní .NET Framework 4.5 `freshness` atribut bude typu `xs:string` a jeho výchozí hodnotu bude `null`.|  
|homeRealm|Domovské sféry zprostředkovatele identity (IP) pro ověřování. Nastaví parametr Wh WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr Wh není zahrnutý v požadavku.|  
|issuer|Identifikátor URI určený vydavatel tokenu. Nastaví základní adresu URL služby WS-Federation žádostí o přihlášení a odhlášení požadavky vyžaduje.|  
|persistentCookiesOnPassiveRedirects|Určuje, zda jsou vydané trvalé soubory cookie pro ověřování. Volitelné. Výchozí hodnota je "false", nejsou vydány soubory cookie.|  
|passiveRedirectEnabled|Určuje, zda WSFAM k automatickému přesměrování neautorizovaných žádostí na služby tokenů zabezpečení. Volitelné. Výchozí hodnota je "PRAVDA", jsou automaticky přesměrováno neautorizovaných žádostí.|  
|Zásady|Adresa URL, která určuje umístění příslušné zásady pro použití na žádostí o přihlášení. Výchozí hodnota je prázdný řetězec. Nastaví parametr wp WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wp není zahrnutý v požadavku.|  
|sféry|Identifikátor URI požadavku sféry. (Identifikátor URI identifikující předávající strany (RP) do služby tokenů zabezpečení (STS).) Nastaví parametr žádosti žádost wtrealm přihlášení WS-Federation. Požadováno.|  
|odpověď|Adresa URL, který adresu, na které aplikace předávající stranu chcete dostávat odpovědi z Security Token Service (STS). Nastaví parametr WS-Federation požádat o přihlášení wreply. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že v požadavku není zahrnutý parametr wreply.|  
|Požadavek|Požadavek vystavování tokenů. Nastaví parametr wreq WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wreq není zahrnutý v požadavku. V požadavku není včetně wreq nebo parametr wreqptr znamená, že služba tokenů zabezpečení ví, jaký druh tokenu k vydání.|  
|requestPtr|Adresu URL, která určuje umístění vystavování tokenů požadavku. Nastaví parametr wreqptr žádosti. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wreqptr není zahrnutý v požadavku. V požadavku není včetně wreq nebo parametr wreqptr znamená, že služba tokenů zabezpečení ví, jaký druh tokenu k vydání.|  
|requireHttps|Určuje, zda komunikace se službou tokenů zabezpečení (STS) musí používat protokol HTTPS. Volitelné. Výchozí hodnota je "PRAVDA", musí používat protokol HTTPS.|  
|prostředek|Identifikátor URI, který identifikuje prostředek přistupuje, předávající strany (RP), na do služby tokenů zabezpečení (STS). Volitelné. Nastaví parametr wres WS-Federation požádat o přihlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wres není zahrnutý v požadavku. **Poznámka:** wres je parametr starší verze. Zadejte `realm` atribut místo toho použít parametr wtrealm.|  
|signInQueryString|Poskytuje bod rozšiřitelnosti zadat parametry dotazu aplikace definovaná v adrese URL žádosti o přihlášení WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry by měl být součástí požadavku. Parametry jsou zadané jako fragment řetězec dotazu, který je v následující podobě: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:** v konfiguračním souboru ' & "znak v řetězci dotazu, musí být určen pomocí jeho odkaz entity `&`.|  
|signOutQueryString|Poskytuje bod rozšiřitelnosti zadat parametry dotazu aplikace definovaná v adrese URL žádosti o přihlášení WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry by měl být součástí požadavku. Parametry jsou zadané jako fragment řetězec dotazu, který je v následující podobě: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:** v konfiguračním souboru ' & "znak v řetězci dotazu, musí být určen pomocí jeho odkaz entity `&`.|  
|signOutReply|Určuje adresu URL, na kterou by měl být klienta přesměruje pomocí služby tokenů zabezpečení (STS) během pasivní odhlašování pomocí protokolu WS-Federation. Nastaví parametr wreply na žádost WS-Federation odhlášení. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry by měl být součástí požadavku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `<wsFederation>` elementu, který chcete konfigurovat výchozí nastavení parametrů služby WS-Federation a výchozí chování pro WSFAM. Nastavení parametru služby WS-Federation definované v části `<wsFederation>` element nastavit ekvivalentní vlastnosti vystavené <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy. Tyto vlastnosti zůstávají stejné pro každý požadavek vydal WSFAM. Můžete změnit parametry WS-Federation dynamicky během požadavku zpracování přidáním obslužných rutin událostí pro události vystavené WSFAM; například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událostí. Další informace najdete v dokumentaci pro <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy.  
  
 `<wsFederation>` Element je reprezentována <xref:System.IdentityModel.Services.Configuration.WSFederationElement> třídy. Samotný objekt konfigurace je reprezentována <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> třídy. Jeden <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instance je nastavený na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objektu, který je přístupný prostřednictvím <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost a poskytuje konfigurace WSFAM.  
  
## <a name="example"></a>Příklad  
 Následují XML `<wsFederation>` element, který určuje nastavení pro WSFAM.  
  
> [!WARNING]
>  V tomto příkladu WSFAM není potřeba používat protokol HTTPS. Důvodem je, že `requireHttps` atributu u `<wsFederation>` element je nastaven `false`. Toto nastavení se nedoporučuje pro většinu produkční prostředí, protože ho může představovat bezpečnostní riziko.  
  
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
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
