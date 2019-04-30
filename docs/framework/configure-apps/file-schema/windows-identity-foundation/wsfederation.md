---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 276f552767897729bf58c6a803669f39c96f09e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790465"
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
|authenticationType.|Identifikátor URI, který určuje typ ověřování. Nastaví parametr wauth požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wauth není zahrnutý v požadavku.|  
|aktuálnost|Požadovaný maximální dobu žádosti o ověření během několika minut. Nastaví parametr wfresh požadavek WS-Federation. Volitelné. Výchozí hodnota je nula. Volitelné. **Upozornění:**  V další vydané verzi rozhraní .NET Framework 4.5 `freshness` atribut budou typu `xs:string` a její výchozí hodnotu bude `null`.|  
|homeRealm|Domovské sféry zprostředkovatele identity (IdP) pro účely ověření. Nastaví parametr Wh požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr Wh není zahrnutý v požadavku.|  
|issuer|Identifikátor URI zamýšlený vydavatel tokenu. Nastaví základní adresu URL WS-Federation žádostí o přihlášení a odhlášení požadavky vyžaduje.|  
|persistentCookiesOnPassiveRedirects|Určuje, zda jsou trvalé soubory cookie vydala na ověřování. Volitelné. Výchozí hodnota je "false", nejsou vysílány soubory cookie.|  
|passiveRedirectEnabled|Určuje, zda je povoleno WSFAM automaticky přesměrovat neoprávněné požadavky služby tokenů zabezpečení. Volitelné. Výchozí hodnota je "true", se automaticky přesměrují neoprávněné požadavky.|  
|Zásady|Adresa URL, která určuje umístění odpovídající zásady pro použití na žádostí o přihlášení. Výchozí hodnota je prázdný řetězec. Nastaví parametr wp požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wp není zahrnutý v požadavku.|  
|Sféra|Identifikátor URI žádající sféru. (Identifikátor URI identifikující předávající strany (RP) do služby tokenů zabezpečení (STS).) Nastaví parametr, který požadavek wtrealm přihlášení WS-Federation požadavku. Povinný parametr.|  
|Odpověď|Adresa URL, která identifikuje adresu, na který aplikaci předávající stranu chtějí dostávat odpovědi z tokenu služba zabezpečení (STS). Nastaví parametr wreply požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wreply není zahrnutý v požadavku.|  
|Požadavek|Požadavek na vystavení tokenu. Nastaví parametr wreq požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wreq není zahrnutý v požadavku. Nezahrnuje v požadavku wreq nebo parametrem wreqptr znamená, že služba tokenů zabezpečení ví, jaký druh tokenu k vydávání.|  
|requestPtr|Adresa URL, která určuje umístění vystavování tokenů požadavku. Nastaví parametr wreqptr požadavku. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametrem wreqptr není zahrnutý v požadavku. Nezahrnuje v požadavku wreq nebo parametrem wreqptr znamená, že služba tokenů zabezpečení ví, jaký druh tokenu k vydávání.|  
|requireHttps|Určuje, jestli komunikaci se službou tokenů zabezpečení (STS) musí používat protokol HTTPS. Volitelné. Výchozí hodnota je "true", musíte použít HTTPS.|  
|prostředek|Identifikátor URI, který identifikuje prostředek přistupuje, předávající strany (RP), položky na službu tokenů zabezpečení (STS). Volitelné. Nastaví parametr wres požadavek WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že parametr wres není zahrnutý v požadavku. **Poznámka:** wres je parametr starší verze. Zadejte `realm` atribut místo toho použít parametr wtrealm.|  
|signInQueryString|Představuje rozšíření bod k určení aplikací definované parametry dotazu v adrese URL žádosti o přihlášení WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry, měly by být součástí požadavku. Parametry jsou zadané jako fragment řetězce dotazu pomocí následujícího formuláře: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru "&" znak v řetězci dotazu musí být zadán pomocí jeho odkaz na entitu, `&`.|  
|signOutQueryString|Představuje rozšíření bod k určení aplikací definované parametry dotazu v adrese URL žádosti o přihlášení WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry, měly by být součástí požadavku. Parametry jsou zadané jako fragment řetězce dotazu pomocí následujícího formuláře: `"param1=value1&param2=value2&param3=value3"` a tak dále. **Poznámka:**  V konfiguračním souboru "&" znak v řetězci dotazu musí být zadán pomocí jeho odkaz na entitu, `&`.|  
|signOutReply|Určuje adresu URL, ke kterému by měla být klient přesměruje pomocí služby tokenů zabezpečení (STS) během pasivní odhlašování přes protokol WS-Federation. Nastaví parametr wreply na žádost o odhlašování přes protokol WS-Federation. Volitelné. Výchozí hodnota je prázdný řetězec, který určuje, že žádné další parametry, měly by být součástí požadavku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Obsahuje nastavení, která konfigurace <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) a <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `<wsFederation>` prvek, který chcete konfigurovat výchozí nastavení parametrů WS-Federation a výchozí chování pro WSFAM. Nastavení parametrů WS-Federation definované v části `<wsFederation>` element nastaven rovnocenné vlastností vystavovaných třídami <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy. Tyto vlastnosti zůstávají stejné pro každý požadavek vystavil WSFAM. Můžete změnit parametry WS-Federation dynamicky během zpracování tak, že přidáte obslužné rutiny událostí pro události vystavené WSFAM; požadavku například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událostí. Další informace najdete v tématu v dokumentaci <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy.  
  
 `<wsFederation>` Prvek je reprezentován <xref:System.IdentityModel.Services.Configuration.WSFederationElement> třídy. Samotný objekt konfigurace je reprezentována <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> třídy. Jediný <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instance je nastavena na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objekt, který je přístupný prostřednictvím <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost a poskytuje konfiguraci pro WSFAM.  
  
## <a name="example"></a>Příklad  
 Zobrazí se následující XML `<wsFederation>` element, který určuje nastavení pro WSFAM.  
  
> [!WARNING]
>  V tomto příkladu WSFAM nevyžaduje k používání protokolu HTTPS. Je to proto, `requireHttps` atribut na `<wsFederation>` prvek je nastaven `false`. Toto nastavení se nedoporučuje pro většinu produkčních prostředí, protože to může představovat bezpečnostní riziko.  
  
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
