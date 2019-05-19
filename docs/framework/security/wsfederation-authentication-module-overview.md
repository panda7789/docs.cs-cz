---
title: Přehled modulu ověřování WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: 0bd6c7432f79894c9e31952b72f3426fc88f9d03
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877195"
---
# <a name="wsfederation-authentication-module-overview"></a>Přehled modulu ověřování WSFederation
Technologie Windows Identity Foundation (WIF) zahrnuje podpory federovaného ověřování v aplikacích ASP.NET prostřednictvím modulu ověřování WS-Federated (WS-FAM). Toto téma vám pomůže pochopit, jak federované ověřování funguje a jak ji používat.  
  
### <a name="overview-of-federated-authentication"></a>Přehled federovaného ověřování  
 Federované ověřování umožňuje Token služby zabezpečení (STS) v jedné doméně důvěryhodnosti předávat informace o ověřování do služby tokenů zabezpečení v jiné doméně důvěryhodnosti při mezi jejich dvěma doménami neexistuje vztah důvěryhodnosti. Příkladem je vidět na následujícím obrázku:  
  
 ![Diagram znázorňující scénář federovaného ověřování.](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Klienta ve vztahu důvěryhodnosti domény Fabrikam odešle požadavek na aplikaci předávající strany (RP) v doméně Contoso vztah důvěryhodnosti.  
  
2. RP přesměruje klienta do služby STS ve vztahu důvěryhodnosti domény Contoso. Tato služba tokenů zabezpečení je vůbec nezná klienta.  
  
3. Služba tokenů zabezpečení Contoso přesměruje klienta do služby STS ve společnosti Fabrikam vztah důvěryhodnosti domény, pomocí kterého vztah důvěryhodnosti domény Contoso má vztah důvěryhodnosti.  
  
4. Služba tokenů zabezpečení společnosti Fabrikam ověřuje identitu klienta a vydá token zabezpečení na službu STS Contoso.  
  
5. Služba tokenů zabezpečení Contoso použije Fabrikam token k vytvoření vlastní token, který je možné RP a odešle předávající straně.  
  
6. RP extrahuje klienta deklarací z tokenu zabezpečení a udělá rozhodnutí o autorizaci.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Modul federovaného ověřování pomocí technologie ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WS-FAM) je modul HTTP, který můžete přidat federovaného ověřování do aplikace ASP.NET. Federované ověřování umožňuje zpracovat STS a umožňuje zaměřit se na psaní obchodní logiky logiku ověřování.  
  
 Konfiguraci WS-služba FAM k určení služby tokenů zabezpečení, ke kterým by měl být přesměrován neověřenými požadavky. Technologie WIF umožňuje ověření uživatele dvěma způsoby:  
  
1. Pasivní přesměrování: Když neověřený uživatel pokusí o přístup k chráněnému prostředku a chcete jednoduše přesměruje je to služby tokenů zabezpečení bez nutnosti přihlašovací stránku, to je ten správný přístup. Služba tokenů zabezpečení ověří identitu uživatele a vydá token zabezpečení, která obsahuje odpovídající deklarace identity pro tohoto uživatele. Tato možnost vyžaduje FAM WS k přidání do kanálu z modulů HTTP. Můžete upravit konfigurační soubor vaší aplikace k používání WS-FAM a provést federaci se službou STS Identity and Access Tool for Visual Studio 2012. Další informace najdete v tématu [Identity and Access Tool for Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2. Můžete volat <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metoda nebo <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> metodu z modelu code-behind přihlašovací stránku ve vaší aplikaci předávající strany.  
  
 V pasivní přesměrování veškerá komunikace se provádí prostřednictvím odpovědi/přesměrování z klienta (obvykle prohlížeče). Služba FAM WS můžete přidat do kanálu HTTP vaší aplikace, kde se sleduje pro neověřené uživatele požadavků a přesměruje uživatele na službu STS je zadat.  
  
 Služba FAM WS také vyvolává několik událostí, které umožňují přizpůsobit jeho funkce v aplikaci technologie ASP.NET.  
  
### <a name="how-the-ws-fam-works"></a>Jak funguje služba FAM WS  
 Služba FAM WS je implementována v <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy. Obvykle přidáte WS-FAM do kanálu HTTP z vaší aplikace předávající strany technologie ASP.NET. Když neověřený uživatel pokusí o přístup k chráněnému prostředku, RP vrátí odpověď HTTP "401 autorizace byl odepřen". WS-FAM zachycuje tuto odpověď místo a umožnil tak klientovi ho přijímat a pak ho přesměruje uživatele na zadanou službu STS. Služba tokenů zabezpečení vydá token zabezpečení, které služba WS-FAM zachycuje znovu. Služba FAM WS použije token k vytvoření instance <xref:System.Security.Claims.ClaimsPrincipal> pro ověřeného uživatele, což umožňuje regulární mechanismy ověřování na rozhraní .NET Framework fungovat.  
  
 Protože HTTP je bezstavové, potřebujeme způsob, jak předcházet opakování této celého procesu pokaždé, když uživatel pokusí přistoupit k jiný chráněný zdroj. Tady <xref:System.IdentityModel.Services.SessionAuthenticationModule> je k dispozici ve. Když služba tokenů zabezpečení vydá token zabezpečení pro uživatele, <xref:System.IdentityModel.Services.SessionAuthenticationModule> také vytvoří tokenu zabezpečení relace pro uživatele a umístí jej do souboru cookie. O následných požadavcích <xref:System.IdentityModel.Services.SessionAuthenticationModule> zachycuje tento soubor cookie a použije ho k rekonstrukci uživatele <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Následující diagram ukazuje celkový tok informací v případě pasivní přesměrování. Požadavek je automaticky přesměrován prostřednictvím služby STS, na navázání přihlašovací údaje bez přihlašovací stránku:  
  
 ![Diagram, který ukazuje, přihlaste se pomocí pasivní přesměrování.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Následující diagram znázorňuje více podrobností, na co se stane, když uživatel se ověřil na službu STS a jejich tokeny zabezpečení jsou zpracovány <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Časování pro zpracování tokenu s pasivní přesměrování](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Následující diagram znázorňuje více podrobností, na co se stane, když tokeny zabezpečení uživatele byl serializován do souborů cookie a jsou zachycena <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![SAM časování diagram zobrazující přihlašování&#45;pomocí ovládacích prvků](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Události  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>a jejich nadřazené třídu <xref:System.IdentityModel.Services.HttpModuleBase>, vyvolat události na různé fáze zpracování požadavku HTTP. Můžete zpracovávat tyto události v `global.asax` souboru aplikace ASP.NET.  
  
- Infrastruktura technologie ASP.NET vyvolá modulu <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metody k inicializaci modulu.  
  
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Událost se vyvolá, když se vyvolá infrastruktury ASP.NET <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metoda poprvé na jeden z vaší aplikace modulů, které jsou odvozeny z <xref:System.IdentityModel.Services.HttpModuleBase>. Tato metoda umožňuje přístup statické <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost, která způsobí, že konfigurace mají být načteny ze souboru Web.config. Tato událost je aktivována pouze při prvním přístupu k této vlastnosti. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Přistupuje prostřednictvím objektu, který se inicializuje z konfigurace <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost v obslužné rutině události. Změna konfigurace předtím, než se použije pro všechny moduly, které můžete pomocí této události. Obslužné rutiny pro tuto událost můžete přidat do metody Application_Start:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Přepíše každého modulu <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> a <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> abstraktní metody. První z těchto metod přidá obslužné rutiny události kanálu ASP.NET, které jsou zajímavé pro modul. Ve většině případů bude stačit výchozí implementace modulu. Inicializuje druhý z těchto metod modulu vlastnosti z jeho <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> vlastnost. (Toto je kopie konfigurace, která byla dříve načtena.) Možná budete muset potlačí tuto metodu za druhé, pokud chcete zajistit podporu Inicializace nové vlastnosti z konfigurace v třídách, které jsou odvozeny z <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> nebo <xref:System.IdentityModel.Services.SessionAuthenticationModule>. V takových případech je také třeba odvozen od odpovídající konfiguraci objektů pro podporu přidání konfigurace vlastnosti; např. z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, nebo <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
- Vyvolá WS-FAM <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> událost, když se zachycuje, který byl vystaví služba STS token zabezpečení.  
  
- Vyvolá WS-FAM <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> událost po ověřila token.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvolá <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> událostí při vytváření tokenu zabezpečení relace pro uživatele.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Vyvolá <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> událost v případě zachycuje následné žádosti pomocí souboru cookie, který obsahuje token relace zabezpečení.  
  
- Předtím, než služba FAM WS přesměruje uživatele na vydavatele, vyvolá <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> událostí. Žádost o přihlášení ke WS-Federation, je k dispozici prostřednictvím <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> vlastnost <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> předané události. Můžete upravit požadavku před odesláním to a vydavatele.  
  
- Vyvolá WS-FAM <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> událost v případě, že je úspěšně zapsána souboru cookie a uživatel je přihlášený.  
  
- Vyvolá WS-FAM <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> událostí každou relaci jako relace se zavírá pro každého uživatele. Není vyvolána, pokud není zavřena relace na straně klienta (například tak, že odstraníte soubor cookie relace). V prostředí jednotného přihlašování služby STS IP požádat o každé RP odhlášení příliš. To se také vyvolat tuto událost s <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> nastavena na `true`.  
  
> [!NOTE]
>  Neměli byste používat <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost během libovolné události vyvolané službou <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> nebo <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Důvodem je, že <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> nastavená po dokončení procesu ověření během události jsou vyvolány během procesu ověřování.  
  
### <a name="configuration-of-federated-authentication"></a>Konfigurace federovaného ověřování  
 Služba WS-FAM a SAM se konfigurují [ \<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) podřízený element konfiguruje výchozí hodnoty pro vlastnosti WS-FAM; jako <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> vlastnost a <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> vlastnost. (Tyto hodnoty můžete změnit na základě žádosti tím, že poskytuje obslužné rutiny pro některé WS-FAM události; například <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Obslužná rutina souboru cookie, který používá SAM se konfiguruje prostřednictvím [ \<z toho důvodu >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) podřízený element. Technologie WIF umožňuje implementované v obslužnou rutinu výchozí soubor cookie <xref:System.IdentityModel.Services.ChunkedCookieHandler> třídu, která může mít velikost bloku dat nastavit pomocí [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) elementu. `<federationConfiguration>` Elementu odkazy <xref:System.IdentityModel.Configuration.IdentityConfiguration>, poskytující konfiguraci pro jiné komponenty technologie WIF používaných v aplikaci, například <xref:System.Security.Claims.ClaimsAuthenticationManager> a <xref:System.Security.Claims.ClaimsAuthorizationManager>. Konfigurace identity může odkazovat explicitně tak, že zadáte pojmenovaná [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek `identityConfigurationName` atribut `<federationConfiguration>` element. Pokud není výslovně odkazována konfigurace identity, použije se výchozí konfigurace identity.  
  
 Následující kód XML ukazuje konfiguraci technologie ASP.NET předávající stranu aplikace. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> a <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> konfigurační oddíly jsou přidány pod `<configSections>` elementu. SAM a služba WS-FAM se přidají do modulů HTTP v rámci `<system.webServer>` / `<modules>` elementu. Nakonec komponenty technologie WIF jsou nakonfigurované v rámci `<system.identityModel>` / `<identityConfiguration>` a `<system.identityModel.services>` / `<federationConfiguration>` elementy. Tato konfigurace určuje obslužná rutina bloku dat souboru cookie, jako je výchozí popisovač souboru cookie a zadané v typ obslužné rutiny souborů cookie není `<cookieHandler>` elementu.  
  
> [!WARNING]
>  V následujícím příkladu jak `requireHttps` atribut `<wsFederation>` elementu a `requireSsl` atribut `<cookieHandler>` elementu `false`. To představuje potenciální ohrožení zabezpečení. V produkčním prostředí by měl nastavit obě tyto hodnoty `true`.  
  
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
- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
