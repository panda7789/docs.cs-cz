---
title: Přehled modulu ověřování WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: 26cd022ded8dddcfcf695c89b3cf4b90d3ceb2ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044938"
---
# <a name="wsfederation-authentication-module-overview"></a>Přehled modulu ověřování WSFederation
Windows Identity Foundation (WIF) zahrnuje podporu federovaného ověřování v aplikacích ASP.NET prostřednictvím modulu WS-federovaného ověřování (WS-FAM). Toto téma vám pomůže pochopit, jak federované ověřování funguje a jak ho používat.  
  
### <a name="overview-of-federated-authentication"></a>Přehled federovaného ověřování  
 Federované ověřování umožňuje, aby služba tokenů zabezpečení (STS) v jedné doméně důvěryhodnosti poskytovala ověřovací informace v jiné doméně důvěryhodnosti v případě, že mezi těmito dvěma doménami existuje vztah důvěryhodnosti. Příklad ukazuje následující obrázek:  
  
 ![Diagram znázorňující scénář federovaného ověřování](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Klient v doméně vztahu důvěryhodnosti Fabrikam odešle požadavek na aplikaci předávající strany (RP) v doméně vztahu důvěryhodnosti společnosti Contoso.  
  
2. RP přesměrovává klienta na službu STS v doméně vztahu důvěryhodnosti společnosti Contoso. Tato služba STS nemá žádné znalosti o klientovi.  
  
3. Společnost Contoso STS přesměruje klienta na službu STS v doméně vztahu důvěryhodnosti Fabrikam, se kterou má důvěryhodná doména contoso vztah důvěryhodnosti.  
  
4. Služba Fabrikam STS ověří identitu klienta a vydá token zabezpečení pro společnost Contoso STS.  
  
5. Společnost Contoso STS používá token Fabrikam k vytvoření vlastního tokenu, který může být použit v RP a odesílá ho do RP.  
  
6. RP extrahuje deklarace identity klienta z tokenu zabezpečení a provede rozhodnutí o autorizaci.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Použití modulu federovaného ověřování s ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-FAM) je modul HTTP, který umožňuje přidat federované ověřování do aplikace ASP.NET. Federované ověřování umožňuje zpracování logiky ověřování službou STS a umožňuje zaměřit se na psaní obchodní logiky.  
  
 Nakonfigurujte WS-FAM a určete službu STS, na kterou by se měly přesměrovat neověřené požadavky. WIF umožňuje ověřit uživatele dvěma způsoby:  
  
1. Pasivní přesměrování: Když se neověřený uživatel pokusí o přístup k chráněnému prostředku a chcete ho jednoduše přesměrovat na službu STS bez vyžadování přihlašovací stránky, jedná se o správný přístup. Služba STS ověří identitu uživatele a vydá token zabezpečení, který obsahuje příslušné deklarace identity pro daného uživatele. Tato možnost vyžaduje, aby se WS-FAM přidal do kanálu modulů HTTP. Nástroj identity and Access Tool for Visual Studio 2012 můžete použít k úpravě konfiguračního souboru aplikace tak, aby používal WS-FAM a federovat se službou STS. Další informace naleznete v tématu [identity and Access Tool for Visual Studio 2012](identity-and-access-tool-for-vs.md).  
  
2. Můžete zavolat <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metodu <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> nebo metodu z kódu na pozadí pro přihlašovací stránku v aplikaci RP.  
  
 V pasivním přesměrování se veškerá komunikace provádí prostřednictvím odpovědi nebo přesměrování od klienta (obvykle v prohlížeči). Do kanálu HTTP vaší aplikace můžete přidat WS-FAM, kde sleduje neověřené požadavky uživatelů a přesměruje uživatele na službu STS, kterou zadáte.  
  
 WS-FAM také vyvolává několik událostí, které umožňují přizpůsobení jeho funkcí v aplikaci ASP.NET.  
  
### <a name="how-the-ws-fam-works"></a>Jak funguje WS-FAM  
 Specifikace WS-FAM je implementována ve <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídě. Obvykle přidáte WS-FAM k kanálu HTTP vaší aplikace ASP.NET RP. Když se neověřený uživatel pokusí o přístup k chráněnému prostředku, RP vrátí odpověď HTTP "autorizace" s odepřením "401". WS-FAM zachycuje tuto odpověď místo toho, aby ji klient přijal, pak přesměruje uživatele na zadanou službu STS. Služba STS vydá token zabezpečení, který WS-FAM znovu zachycuje. WS-FAM používá token k vytvoření instance <xref:System.Security.Claims.ClaimsPrincipal> pro ověřeného uživatele, což umožňuje regulárním mechanismům pro .NET Framework autorizaci funkce.  
  
 Vzhledem k tomu, že HTTP je bezstavový, potřebujeme způsob, jak se vyhnout opakování celého procesu pokaždé, když se uživatel pokusí o přístup k jinému chráněnému prostředku. Zde je místo, <xref:System.IdentityModel.Services.SessionAuthenticationModule> kde se nachází. Když služba STS vydá token zabezpečení pro uživatele, <xref:System.IdentityModel.Services.SessionAuthenticationModule> vytvoří také token zabezpečení relace pro uživatele a vloží ho do souboru cookie. Při následném požadavku <xref:System.IdentityModel.Services.SessionAuthenticationModule> zachycuje tento soubor cookie a použije ho k rekonstrukci <xref:System.Security.Claims.ClaimsPrincipal>uživatele.  
  
 Následující diagram znázorňuje Celkový tok informací v pasivním případu přesměrování. Požadavek se automaticky přesměruje prostřednictvím služby STS, aby se navázaly přihlašovací údaje bez přihlašovací stránky:  
  
 ![Diagram, který zobrazuje přihlášení pomocí pasivního přesměrování.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Následující diagram zobrazuje více podrobností o tom, co se stane, když uživatel ověřil službu STS a jejich tokeny zabezpečení jsou zpracovávány <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>pomocí:  
  
 ![Načasování zpracování tokenu pomocí pasivního přesměrování](./media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Následující diagram zobrazuje více podrobností o tom, co se stane, když jsou tokeny zabezpečení uživatele serializovány do souborů cookie a jsou zachyceny pomocí <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Časový diagram Sam ukazující přihlášení&#45;pomocí ovládacích prvků](./media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Události  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>a jejich nadřazená <xref:System.IdentityModel.Services.HttpModuleBase>třída, vyvolávají události v různých fázích zpracování požadavku HTTP. Tyto události můžete zpracovat v `global.asax` souboru aplikace ASP.NET.  
  
- Infrastruktura ASP.NET vyvolá <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metodu modulu pro inicializaci modulu.  
  
- Událost se vyvolá, když infrastruktura ASP.NET vyvolá <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metodu poprvé na jednom z modulů aplikace, které jsou odvozeny z <xref:System.IdentityModel.Services.HttpModuleBase>. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Tato metoda přistupuje ke statické <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnosti, která způsobuje, že konfigurace byla načtena ze souboru Web. config. Tato událost je aktivována pouze při prvním otevření této vlastnosti. Objekt, který je inicializován z konfigurace, je k dispozici <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> prostřednictvím vlastnosti v obslužné rutině události. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Tuto událost můžete použít ke změně konfigurace předtím, než se použije pro všechny moduly. Do metody Application_Start lze přidat obslužnou rutinu pro tuto událost:  
  
    ```csharp
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Každý modul Přepisuje rozhraní <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> a <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> abstraktní metody. První z těchto metod přidá obslužné rutiny pro události kanálu ASP.NET, které mají zájem o modul. Ve většině případů bude stačit výchozí implementace modulu. Druhá z těchto metod inicializuje vlastnosti modulu z jeho <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> vlastnosti. (Jedná se o kopii konfigurace, která byla dříve načtena.) Tato druhá metoda může být nutné přepsat, pokud chcete podporovat inicializaci nových vlastností z konfigurace tříd, které jsou odvozeny z <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> nebo. <xref:System.IdentityModel.Services.SessionAuthenticationModule> V takových případech byste také museli odvozovat z příslušných objektů konfigurace pro podporu vlastností přidané konfigurace; například z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>nebo. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>  
  
- WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> událost, když zachycuje token zabezpečení, který byl vydán službou STS.  
  
- WS-FAM vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> událost poté, co ověří token.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvoláudálostpřivytvořenítokenu<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> zabezpečení relace pro uživatele.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvoláudálost,kdyžzachycujenáslednéžádostisesouboremcookie,který<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> obsahuje token zabezpečení relace.  
  
- Před tím, než WS-FAM přesměruje uživatele na vystavitele, vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událost. Požadavek na přihlášení ke službě WS-Federation je k dispozici <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> prostřednictvím vlastnosti <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> předané události. Před odesláním tohoto požadavku vystaviteli se můžete rozhodnout tuto žádost upravit.  
  
- WS-FAM vyvolá událost, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> když se soubor cookie úspěšně zapíše a uživatel je přihlášený.  
  
- WS-FAM vyvolává <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> událost jednou pro každou relaci, protože relace je pro každého uživatele uzavřená. Není vyvolána, pokud je relace ukončena na straně klienta (například odstraněním souboru cookie relace). V prostředí jednotného přihlašování může IP-STS požádat jednotlivé RP, aby se odhlásili. Tato akce také vyvolá tuto událost s <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> nastavením na. `true`  
  
> [!NOTE]
> <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> Vlastnost byste neměli používat při žádné události <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> vyvolané nebo <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Důvodem je to <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> , že je nastaven po procesu ověřování, zatímco události jsou vyvolány během procesu ověřování.  
  
### <a name="configuration-of-federated-authentication"></a>Konfigurace federovaného ověřování  
 WS-FAM a Sam jsou konfigurovány prostřednictvím [ \<elementu federationConfiguration >](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) . Podřízený element <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> wsFederation > konfiguruje výchozí hodnoty vlastností WS-FAM, jako je například vlastnost a vlastnost. [ \<](../configure-apps/file-schema/windows-identity-foundation/wsfederation.md) (Tyto hodnoty lze změnit na základě jednotlivých požadavků poskytnutím obslužných rutin pro některé události WS-FAM; například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Obslužná rutina souborů cookie, kterou používá Sam, je konfigurována [ \<](../configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) prostřednictvím podřízeného prvku cookieHandler >. WIF poskytuje výchozí obslužnou rutinu souborů cookie implementovanou <xref:System.IdentityModel.Services.ChunkedCookieHandler> ve třídě, která může mít svou velikost bloku dat nastavenou [ \<prostřednictvím elementu chunkedCookieHandler >](../configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) . Element odkazuje na <xref:System.Security.Claims.ClaimsAuthenticationManager> ,který<xref:System.Security.Claims.ClaimsAuthorizationManager>poskytuje konfiguraci pro jiné komponenty WIF používané v aplikaci, jako jsou a. <xref:System.IdentityModel.Configuration.IdentityConfiguration> `<federationConfiguration>` Na konfiguraci identity se může explicitně odkazovat zadáním pojmenovaného [ \<> elementu IdentityConfiguration](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) v `identityConfigurationName` atributu `<federationConfiguration>` elementu. Pokud se na konfiguraci identity explicitně neodkazuje, použije se výchozí konfigurace identity.  
  
 Následující kód XML ukazuje konfiguraci aplikace předávající strany ASP.NET (RP). Konfigurační oddíly <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> a jsou přidány pod element.`<configSections>` <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> Sam a WS-FAM jsou přidány do modulů http pod `<system.webServer>` / `<modules>` prvkem. Nakonec komponenty WIF jsou nakonfigurovány v rámci `<system.identityModel>` / `<identityConfiguration>` prvků `<system.identityModel.services>` a / `<federationConfiguration>` . Tato konfigurace Určuje popisovač souboru cookie v bloku dat, protože je to výchozí obslužná rutina souborů cookie a v `<cookieHandler>` elementu není zadaný typ obslužné rutiny souborů cookie.  
  
> [!WARNING]
> V následujícím `requireHttps` příkladu je atribut `requireSsl` `<wsFederation>` elementu `false`i atribut elementu. `<cookieHandler>` To představuje potenciální bezpečnostní hrozbu. V produkčním prostředí by měly být obě tyto `true`hodnoty nastaveny.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<federationConfiguration>](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
