---
title: "Přehled modulu ověřování WSFederation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ea17e384ecb4536ed544e3b874631db6fe54e0e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wsfederation-authentication-module-overview"></a>Přehled modulu ověřování WSFederation
Windows Identity Foundation (WIF) zahrnuje podpory federovaného ověřování v aplikacích ASP.NET prostřednictvím modulu ověřování WS-Federated (WS-služba FAM). Toto téma vám pomůže pochopit, jak federovaného ověřování funguje a jak ji používat.  
  
### <a name="overview-of-federated-authentication"></a>Přehled federovaného ověřování  
 Federované ověřování umožňuje zabezpečení tokenu služby (STS) v jedné doméně vztah důvěryhodnosti k poskytnutí informací ověřování služby tokenů zabezpečení v jiné doméně vztahu důvěryhodnosti, pokud je mezi těmito dvěma doménami vztah důvěryhodnosti. Příkladem je znázorněno na následujícím obrázku.  
  
 ![Scénář ověřování federace](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1.  Klienta ve vztahu důvěryhodnosti domény Fabrikam odešle požadavek na aplikaci předávající strany (RP) v doméně Contoso vztah důvěryhodnosti.  
  
2.  RP přesměruje klienta do služby tokenů zabezpečení v doméně Contoso vztah důvěryhodnosti. Tato služba tokenů zabezpečení nemá žádné informace o klientovi.  
  
3.  Služba tokenů zabezpečení Contoso přesměruje klienta do služby tokenů zabezpečení v doméně Fabrikam vztahu důvěryhodnosti, pomocí kterého vztahu důvěryhodnosti domény Contoso má vztah důvěryhodnosti.  
  
4.  Služba tokenů zabezpečení Fabrikam ověří identitu klienta a vydá token zabezpečení na službu STS Contoso.  
  
5.  Služba tokenů zabezpečení Contoso použije Fabrikam token k vytvoření vlastního tokenu, které mohou být využívána RP a odešle ji do RP.  
  
6.  RP extrahuje klienta deklarací z tokenu zabezpečení a provádí rozhodnutí o autorizaci.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Modul federovaného ověřování pomocí technologie ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-služba FAM) je modul protokolu HTTP, která umožňuje přidat federovaného ověřování pro [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace. Federované ověřování umožňuje zpracovávat služby tokenů zabezpečení a vám umožní soustředit na obchodní logiku zápis logiku ověřování.  
  
 Můžete nakonfigurovat WS-služba FAM k určení tokenů zabezpečení, které chcete použít k přesměrování neověřené požadavky. WIF umožňuje ověření uživatele dvěma způsoby:  
  
1.  Pasivní přesměrování: když neověřený uživatel pokusí o přístup k chráněnému prostředku a chcete jednoduše přesměruje je to služby tokenů zabezpečení bez nutnosti přihlašovací stránku a pak toto je správný přístup. Služba tokenů zabezpečení ověřuje identitu uživatele a vydá token zabezpečení, který obsahuje odpovídající deklarace identity pro daného uživatele. Tato možnost vyžaduje WS-služba FAM k přidání do modulů HTTP v kanálu. Identita a přístup pro sadu Visual Studio 2012 můžete použít k úpravě souboru konfigurace aplikace k používání protokolu WS-služba FAM a vytvořit federaci s služby tokenů zabezpečení. Další informace najdete v tématu [identita a přístup pro sadu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Můžete volat <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metoda nebo <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> z modelu code-behind metodu pro přihlašovací stránku ve vaší aplikaci RP.  
  
 V pasivním přesměrování veškerá komunikace probíhá prostřednictvím odpovědi či přesměrování z klienta (obvykle prohlížeč). Služba WS-FAM můžete přidat do kanálu vaší aplikace HTTP, kde ji sleduje pro neověřené uživatele požadavky a přesměruje uživatele na službu STS zadáte.  
  
 Služba WS-FAM také vyvolá několik událostí, které umožňují přizpůsobit její funkce v [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace.  
  
### <a name="how-the-ws-fam-works"></a>Jak funguje služba FAM WS  
 Služba WS-FAM je implementována ve <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy. Obvykle WS-služba FAM přidáte do kanálu HTTP z vaší [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP aplikace. Když neověřený uživatel pokusí o přístup k chráněnému prostředku, RP vrátí odpověď HTTP "401 autorizace byl odepřen". Služba WS-FAM zachycuje této odpovědi namísto umožnil tak klientovi ji přijmou a potom ho přesměruje uživatele na zadané služby tokenů zabezpečení. Služba tokenů zabezpečení vydává tokeny zabezpečení, které služba WS-FAM zachycuje znovu. Služba WS-FAM použije token pro vytvoření instance <xref:System.Security.Claims.ClaimsPrincipal> ověřeného uživatele, což umožňuje regular [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] mechanismy ověřování fungovat.  
  
 Vzhledem k tomu, že HTTP bezstavové, potřebujeme způsob, jak se vyhnout opakováním tohoto celého procesu pokaždé, když se uživatel pokusí o přístup k jiné chráněného prostředku. To je, kdy <xref:System.IdentityModel.Services.SessionAuthenticationModule> odeslán. Když služba tokenů zabezpečení vydá token zabezpečení pro uživatele, <xref:System.IdentityModel.Services.SessionAuthenticationModule> také vytvoří token zabezpečení relace pro uživatele a vloží ho do souboru cookie. Na další požadavky <xref:System.IdentityModel.Services.SessionAuthenticationModule> zachycuje tento soubor cookie a použije ho k rekonstrukci uživatele <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Následující diagram znázorňuje celkové toku informací v případě, že pasivní přesměrování. Je žádost přesměrována automaticky prostřednictvím služby tokenů zabezpečení vytvořit přihlašovací údaje bez přihlašovací stránky:  
  
 ![Diagram časování pro přihlašování & č. 45; pomocí pasivní přesměrování](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 Následující diagram znázorňuje podrobněji na co se stane, když uživatel byl ověřen na službu STS a jejich tokeny zabezpečení jsou zpracovány <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Časování pro zpracování tokenu s pasivní přesměrování](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Následující diagram znázorňuje podrobněji na co se stane, když tokeny zabezpečení uživatele byl serializován do souborů cookie a jsou zachycen <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![SAM časování diagram znázorňující přihlašovací & č. 45; v použití ovládacích prvků](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Události  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>a jejich nadřazené třídy <xref:System.IdentityModel.Services.HttpModuleBase>, vyvolávání událostí v různých fázích zpracování požadavku HTTP. Dokáže zpracovat tyto události v `global.asax` soubor vaší [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace.  
  
-   Infrastruktury ASP.NET vyvolá modulu <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metoda k chybě při inicializaci modulu.  
  
-   <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Událost se vyvolá, když vyvolá infrastruktury ASP.NET <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metoda poprvé na jeden z modulů aplikace, které jsou odvozeny od <xref:System.IdentityModel.Services.HttpModuleBase>. Tato metoda umožňuje přístup statických <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost, což způsobí, že konfigurace být načtená ze souboru Web.config. Tato událost je aktivována pouze při prvním získat přístup k této vlastnosti. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Objekt, který je inicializován ze konfigurace je možné přistupovat prostřednictvím <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost v obslužné rutiny události. Tato událost můžete použít ke změně konfigurace předtím, než se použije pro všechny moduly. Obslužnou rutinu pro tuto událost můžete přidat do metody Application_Start:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Každý modul přepsání <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> a <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> abstraktní metody. První z těchto metod přidá obslužné rutiny pro události kanálu ASP.NET, které jsou důležité pro modul. Ve většině případů bude stačit výchozí implementace modulu. Druhá z těchto metod inicializuje vlastnosti modulu z jeho <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost. (Toto je kopie konfigurace, která byla načtena dříve). Budete muset přepsání této druhé metody, pokud chcete zajistit podporu Inicializace nové vlastnosti z konfigurace v třídy, které jsou odvozeny od <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> nebo <xref:System.IdentityModel.Services.SessionAuthenticationModule>. V takových případech by také potřebujete odvozena od objekty odpovídající konfiguraci pro podporu přidání konfigurační vlastnosti; například z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, nebo <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   Služba WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> událost v případě zachycuje token zabezpečení, který byl vystaven službou tokenů zabezpečení.  
  
-   Služba WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> událostí po ověřila token.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvolá <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> událost v případě, že vytvoří token zabezpečení relace pro uživatele.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvolá <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> událost v případě zachycuje následných žádostí pomocí souboru cookie, který obsahuje token zabezpečení relace.  
  
-   Předtím, než služba WS-FAM přesměruje uživatele na vystavitele, vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událostí. Je k dispozici prostřednictvím služby WS-Federation přihlašovací požadavek <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> vlastnost <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> předán v události. Můžete upravit žádost před odesíláním to vystavitele.  
  
-   Služba WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> událost v případě, že soubor cookie je úspěšně zapsána a je přihlášený uživatel.  
  
-   Služba WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> událostí jednou relace jako relace dochází k uzavření pro každého uživatele. Není vyvolána, pokud relace je ukončena na straně klienta (například odstraněním souboru cookie relace). V prostředí, jednotné přihlašování tokenů zabezpečení IP může požádat o každé RP se odhlásíte, příliš. Tato událost to bude zároveň vyvolává s <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> nastavena na `true`.  
  
> [!NOTE]
>  Neměli byste používat <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost během všechny události vyvolané <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> nebo <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Důvodem je, že <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> je nastavena po dokončení procesu ověřování, přičemž události jsou vyvolány během procesu ověřování.  
  
### <a name="configuration-of-federated-authentication"></a>Konfigurace federovaného ověřování  
 Služba WS-FAM a SAM se konfigurují prostřednictvím [ \<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) podřízený element konfiguruje výchozí hodnoty pro vlastnosti Služba WS-FAM; jako <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> vlastnost a <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> vlastnost. (Tyto hodnoty lze změnit na základě žádosti tím, že poskytuje obslužné rutiny pro některé události Služba WS-FAM; například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Obslužná rutina souboru cookie, který je používán správce zabezpečení účtů se konfigurují prostřednictvím [ \<cookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) podřízený element. WIF poskytuje výchozí soubor cookie obslužnou rutinu implementované v <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídu, která může mít jeho velikost bloku nastavit pomocí [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) element. `<federationConfiguration>` Element odkazy <xref:System.IdentityModel.Configuration.IdentityConfiguration>, který poskytuje konfiguraci pro jiné komponenty WIF použít v aplikaci, například <xref:System.Security.Claims.ClaimsAuthenticationManager> a <xref:System.Security.Claims.ClaimsAuthorizationManager>. Konfigurace identity může být výslovně odkazována zadáním pojmenovaná [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element v `identityConfigurationName` atribut `<federationConfiguration>` elementu. Pokud není výslovně odkazována konfigurace identity, použije se výchozí konfigurace identity.  
  
 Následující kód XML znázorňuje konfiguraci technologie ASP.NET předávající stranu aplikace. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> a <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> konfiguračních oddílů, které se přidají pod `<configSections>` elementu. SAM a služba WS-FAM jsou přidány do modulů HTTP v části `<system.webServer>` / `<modules>` element. Nakonec jsou komponenty WIF nakonfigurované v části `<system.identityModel>` / `<identityConfiguration>` a `<system.identityModel.services>` / `<federationConfiguration>` elementy. Tato konfigurace určuje obslužná rutina soubor cookie rozdělený, jako je výchozí popisovač souboru cookie a typu souboru cookie obslužná rutina zadaná v není `<cookieHandler>` elementu.  
  
> [!WARNING]
>  V následujícím příkladu jak `requireHttps` atribut `<wsFederation>` elementu a `requireSsl` atribut `<cookieHandler>` element jsou `false`. To představuje potenciální ohrožení zabezpečení. V produkčním prostředí, měli nastavit obě tyto hodnoty `true`.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 [\<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
