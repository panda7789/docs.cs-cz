---
title: Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: 645fd09de91d8190384faea9df2ef18511162c2f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834524"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5

## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF) 3,5 a 4,5.

## <a name="overview"></a>Přehled

Windows Identity Foundation (WIF) byl původně vydaný v časovém rámci .NET 3,5 SP1. Tato verze WIF se označuje jako WIF 3,5. Byl vydán jako samostatný modul runtime a sada SDK, což znamenalo, že každý počítač, ve kterém byla spuštěná aplikace s podporou WIF, musel mít nainstalovaný modul WIF runtime a vývojáři museli stáhnout a nainstalovat sadu SDK WIF pro získání šablon a nástrojů sady Visual Studio, které jsou povolené. vývoj aplikací s podporou WIF Od verze .NET 4,5 se WIF plně integruje do .NET Framework. Samostatný modul runtime již není potřeba a nástroje WIF lze nainstalovat do sady Visual Studio 2012 pomocí Správce rozšíření sady Visual Studio. Tato verze WIF se označuje jako WIF 4,5.

Integrace WIF do .NET vyžadovala několik změn na povrchu rozhraní API WIF. WIF 4,5 obsahuje nové obory názvů, některé změny konfiguračních prvků a nové nástroje pro Visual Studio. V tomto tématu najdete pokyny, které vám pomůžou migrovat aplikace sestavené pomocí WIF 3,5 na WIF 4,5. Můžou nastat situace, kdy potřebujete spouštět starší verze aplikací sestavené pomocí WIF 3,5 na počítačích se systémem Windows 8 nebo Windows Server 2012. V tomto tématu najdete taky pokyny, jak povolit WIF 3,5 pro tyto operační systémy.

## <a name="changes-required-for-wif-45"></a>Změny požadované pro WIF 4,5

Tato část popisuje změny, které jsou potřeba k migraci aplikace v WIF 3,5 na WIF 4,5.

### <a name="assembly-and-namespace-changes"></a>Změny sestavení a oboru názvů

V WIF 3,5 všechny třídy WIF byly obsaženy v sestavení `Microsoft.IdentityModel` (Microsoft. identitymicrosoft. IdentityModel. dll). V WIF 4,5 třídy WIF byly rozděleny mezi následující sestavení: `mscorlib` (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) a `System.ServiceModel` (System. ServiceModel. dll).

Třídy WIF 3,5 byly obsaženy v jednom z `Microsoft.IdentityModel` obory názvů; například `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`a tak dále. V WIF 4,5 jsou nyní třídy WIF rozloženy mezi obory názvů [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) , oborem názvů <xref:System.Security.Claims?displayProperty=nameWithType> a oborem názvů <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Kromě této reorganizace byly některé třídy WIF 3,5 v WIF 4,5 vynechány.

Následující tabulka uvádí některé z důležitějších oborů názvů WIF 4,5 a druh tříd, které obsahují. Podrobnější informace o tom, jak se obory názvů mapují mezi WIF 3,5 a WIF 4,5 a o oborech názvů a třídách, které byly vyřazeny v WIF 4,5, najdete v tématu [mapování oboru názvů mezi WIF 3,5 a WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|Obor názvů WIF 4,5|Popis|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Obsahuje třídy, které reprezentují transformační soubory souborů cookie, služby tokenů zabezpečení a specializované čtečky slovníku XML. Obsahuje třídy z následujících oborů názvů WIF 3,5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`a `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Obsahuje třídy, které reprezentují deklarace identity, identity založené na deklaracích, objekty zabezpečení založené na deklaracích identity a další artefakty modelu identity založené na deklaracích identity. Obsahuje třídy z oboru názvů `Microsoft.IdentityModel.Claims`.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Obsahuje třídy, které reprezentují tokeny zabezpečení, obslužné rutiny tokenů zabezpečení a další artefakty tokenů zabezpečení. Obsahuje třídy z následujících oborů názvů WIF 3,5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`a `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Obsahuje třídy, které se používají v pasivních scénářích (WS-Federation). Obsahuje třídy z oboru názvů `Microsoft.IdentityModel.Web`.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Třídy, které představují kontrakty WCF, kanály, hostitele služeb a jiné artefakty, které se používají ve scénářích aktivní (WS-Trust), jsou teď v tomto oboru názvů. V WIF 3,5 byly tyto třídy v oboru názvů `Microsoft.IdentityModel.Protocols.WSTrust`.|

> [!IMPORTANT]
> Následující obory názvů `System.IdentityModel` obsahují třídy, které implementují model identity založené na deklaracích WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při sestavování řešení založených na WIF byste neměli v těchto třech oborech názvů používat třídy.

### <a name="changes-due-to-net-integration"></a>Změny v důsledku integrace rozhraní .NET

WIF je teď integrovaný do .NET Framework. Většina identit a hlavních tříd .NET je teď odvozená od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Výsledkem jsou následující změny v WIF 4,5:

- Třídy WIF, které reprezentují deklarace identity, identity a objekty zabezpečení, nyní existují v oboru názvů <xref:System.Security.Claims?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > Obor názvů <xref:System.IdentityModel.Claims?displayProperty=nameWithType> obsahuje třídy, které reprezentují artefakty v modelu identity založeném na deklaracích identity WCF. Mnohé z těchto tříd mají názvy, které jsou stejné jako třídy WIF; například `Claims`. Nepoužívejte tyto třídy při vytváření řešení založených na WIF.

- Identity a objekty zabezpečení .NET se teď odvozují přímo z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, které reprezentují identity a objekty zabezpečení založené na deklaracích. Z tohoto důvodu rozhraní WIF 3,5 `IClaimsIdentity` a `IClaimsPrincipal` už nejsou potřeba a nejsou k dispozici v WIF 4,5.

- Because.NET identity a hlavní třídy, jako jsou <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> a <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> nyní jsou odvozeny z <xref:System.Security.Claims.ClaimsIdentity> a <xref:System.Security.Claims.ClaimsPrincipal>, mají integrované funkce deklarací identity. Z tohoto důvodu již nepotřebujete identitu specifickou pro deklarace identity a základní třídy, jako je například `WindowsClaimsIdentity` a `WindowsClaimsPrincipal`, které byly přítomny v WIF 3,5, a neexistují v WIF 4,5.

### <a name="other-changes-to-wif-functionality"></a>Další změny WIF funkcí

Kromě změn oboru názvů a změn v důsledku integrace s .NET se v WIF 4,5 následující obecné změny WIF funkce.

- Třída `Microsoft.IdentityModel.ExceptionMapper`, která poskytuje funkce, které vám umožnily mapovat výjimky na konkrétní chyby protokolu SOAP, se odeberou.

- Došlo k výraznému snížení povrchu výjimky.

- Bylo odebráno mnoho tříd definovaných konstantami protokolu nebo WS-*. Například třída `Microsoft.IdentityModel.WSAddressing10Constants`, která definuje konstanty související s WS-Addressing 1,0.

- Odeberou se deklarace identity na službu tokenů systému Windows (C2WTS) a přidružené třídy v oboru názvů `Microsoft.IdentityModel.WindowsTokenService`.

### <a name="wif-configuration-changes"></a>Změny konfigurace WIF

Mnohé změny v konfiguračním souboru byly způsobeny aktualizacemi oboru názvů v WIF 4,5. Zvažte například následující položku WIF 3,5 v části `<httpModules>` a přidejte do aplikace Správce ověřování WS-Federation.

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Tato položka se v WIF 4,5 aktualizovala tak, aby zahrnovala nové obory názvů a verzi sestavení:

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

Následující seznam uvádí hlavní změny konfiguračního souboru pro WIF 4,5.

- Oddíl `<microsoft.identityModel>` je teď oddíl [\<System. identityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) .

- Element `<service>` je nyní [\<IdentityConfiguration prvek >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) .

- K určení nastavení, které řídí chování v pasivních scénářích (WS-Federation), bylo přidáno nové oddílu [\<System. IdentityModel. services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).

- Element [\<federationConfiguration >](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) a jeho podřízené prvky byly přesunuty z prvku `<service>` v WIF 3,5 na nový element `<system.identityModel.services>`.

- Několik prvků, které mohou být zadány na úrovni služby přímo pod elementem `<service>` v WIF 3,5, bylo omezeno na zadání v [\<securityTokenHandlerConfiguration >](../configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. (Můžou se pořád zadat pod [\<identityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu v WIF 4,5 kvůli zpětné kompatibilitě.)

Úplný seznam elementů konfigurace WIF 4,5 najdete v tématu [schéma konfigurace WIF](../configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Změny nástrojů sady Visual Studio

Sada WIF 3,5 SDK nabídla samostatný federační nástroj soubor FedUtil. exe (soubor FedUtil), který můžete použít k externí správě identit v aplikacích s podporou WIF na službu tokenů zabezpečení (STS). Tento nástroj přidal do konfiguračního souboru aplikace nastavení WIF, aby aplikace mohla získávat tokeny zabezpečení z jedné nebo více STS, a byla v aplikaci Visual Studio prostřednictvím **odkazu na službu tokenů služby STS** . Soubor FedUtil se nedodává s WIF 4,5. Místo toho WIF 4,5 podporuje nové rozšíření sady Visual Studio s názvem identity and Access Tool for Visual Studio 2012, které můžete použít k úpravě konfiguračního souboru vaší aplikace pomocí nastavení WIF, které je potřeba pro externí správu identit na službu STS. Nástroj identity and Access také implementuje službu STS nazvanou Local STS, kterou můžete použít k otestování aplikací s podporou WIF. V mnoha případech tato funkce obviates nutnost vytvářet vlastní STS, které byly často nezbytné v WIF 3,5 pro testování řešení ve vývoji. Z tohoto důvodu šablony STS již nejsou podporovány v aplikaci Visual Studio 2012; třídy, které podporují vývoj STS, jsou však stále k dispozici v WIF 4,5.

Nástroj identity and Access můžete nainstalovat z Správce rozšíření a aktualizací v aplikaci Visual Studio nebo si ho můžete stáhnout z následující stránky v galerii kódu: [Nástroj identita and Access Tool for Visual Studio 2012 v galerii kódu](https://go.microsoft.com/fwlink/?LinkID=245849). Změny nástrojů sady Visual Studio jsou shrnuty v následujícím seznamu:

- Funkce Přidat odkaz na službu STS se odebere. Nahrazení je nástroj Identity and Access.

- Šablony služby TOKENů sady Visual Studio se odeberou. Pomocí místní služby STS, která je k dispozici prostřednictvím nástroje Identity and Access Tool, můžete testovat řešení identity, která vyvíjíte pomocí WIF. Místní konfiguraci služby STS je možné upravit tak, aby se přizpůsobily deklarace identity, které obsluhuje.

- Nástroj pro samostatné federace (soubor FedUtil) není v WIF 4,5 k dispozici. Pomocí nástroje Identity and Access můžete změnit konfigurační soubory na externí správu identit na službu STS.

Další informace o nástroji Identity and Access naleznete v tématu [identity and Access Tool for Visual Studio 2012](identity-and-access-tool-for-vs.md).

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Scénáře pasivního (WS-Federation):

- Třídy, které podporují pasivní scénáře, byly přesunuty do oboru názvů <xref:System.IdentityModel.Services?displayProperty=nameWithType>. V WIF 3,5 byly tyto třídy v oboru názvů `Microsoft.IdentityModel.Web`.

- Třídy v oboru názvů `Microsoft.IdentityModel.Web.Configuration` byly přesunuty do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Tyto třídy reprezentují objekty specifické pro konfiguraci v pasivních scénářích.

- `FederatedPassiveSignInControl` už není podporovaný. všechny třídy v oboru názvů `Microsoft.IdentityModel.Web.Controls` byly odebrány z WIF 4,5.

- Funkce odhlášení modulu WS-Federation Authentication Module (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) se liší od WIF 3,5. Další podrobnosti o tom, jak funguje odhlašování v WIF 4,5, najdete v tématu <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídy.

### <a name="active-wcfws-trust-scenarios"></a>Scénáře aktivních (WCF/WS-Trust):

- Obor názvů `Microsoft.IdentityModel.Protocols.WSTrust` byl v WIF 4,5 rozdělen hlavně na dva obory názvů. Třídy, které představují artefakty, které jsou specifické pro protokol WS-Trust, jsou nyní v <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. To zahrnuje třídy jako <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Třídy, které představují kontrakty služby, kanály, hostitele služeb a další artefakty, které se podílejí na používání WS-Trust v aplikacích WCF, se přesunuly na <xref:System.ServiceModel.Security?displayProperty=nameWithType>; například rozhraní <xref:System.ServiceModel.Security.IWSTrust13AsyncContract>.

- Konfigurace aplikace WCF pro použití WIF byla výrazně zjednodušená. Dřív se `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` muselo přidat jako rozšíření chování a tato funkce se pak použila k klínu WIF do chování služby zadáním elementu `<federatedServiceHostConfiguration>`. WIF 4,5 byl s WCF úzce integrován. Nyní povolíte WIF ve službě WCF zadáním atributu `useIdentityConfiguration` na `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` elementu jako v následujícím kódu XML:

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- V WIF 4,5 musí být na hostiteli služby zadaný certifikát služby používaný aktivní službou (WCF). V části Konfigurace to můžete provést prostřednictvím `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>`/`<serviceCertificate>` prvku, jak je znázorněno v předchozím příkladu. V WIF 3,5 je možné zadat certifikát služby prostřednictvím podřízeného elementu `<serviceCertificate>` `<service>` elementu WIF. Tato funkce neexistuje v WIF 4,5; místo toho zadejte `<serviceCertificate>` element pod `<serviceCredentials>` elementu.

- Třídy používané pro klín WIF 3,5 do WCF již neexistují. To zahrnuje následující třídy v oboru názvů `Microsoft.IdentityModel.Tokens`: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`a `IdentityModelServiceAuthorizationManager`a také třídu `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement`.

## <a name="enabling-wif-35-in-windows-8"></a>Povolení WIF 3,5 ve Windows 8

Vzhledem k tomu, že WIF 4,5 je součástí .NET 4,5, je automaticky povolen na počítačích se systémy Windows 8 a Windows Server 2012 a aplikace vytvořené pomocí WIF 4,5 budou ve výchozím nastavení spouštěny ve Windows 8 nebo Windows Serveru 2012. Je ale možné, že budete muset spustit aplikace vytvořené pomocí WIF 3,5 na počítači se systémem Windows 8 nebo Windows Server 2012. V takovém případě musíte povolit WIF 3,5 na cílovém počítači. V počítači se systémem Windows 8 to můžete provést pomocí nástroje pro obsluhu a správu bitových kopií (DISM) pro nasazení. V počítači se systémem Windows Server 2012 můžete použít nástroj DISM nebo můžete použít rutinu `Add-WindowsFeature` prostředí Windows PowerShell. V obou případech lze příslušné příkazy vyvolat buď na příkazovém řádku, nebo v prostředí Windows PowerShell.

Následující příkazy ukazují, jak používat nástroj DISM z příkazového řádku nebo zevnitř prostředí Windows PowerShell. Ve výchozím nastavení je modul PowerShellu DISM součástí systémů Windows 8 a Windows Server 2012 a není nutné ho importovat. Další informace o používání nástroje DISM v prostředí Windows PowerShell najdete v tématu [použití nástroje DISM v prostředí Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).

Povolení WIF 3,5 pomocí nástroje DISM:

```console
dism /online /enable-feature:windows-identity-foundation
```

Zakázání WIF 3,5 pomocí nástroje DISM:

```console
dism /online /disable-feature:windows-identity-foundation
```

Chcete-li zjistit, které funkce jsou povoleny nebo zakázány, pomocí nástroje DISM:

```console
dism /online /get-features
```

Případně můžete v počítačích se systémem Windows Server 2012 povolit WIF 3,5 pomocí rutiny Windows PowerShellu `Add-WindowsFeature`. Pokud to chcete provést z příkazového řádku, můžete zadat následující příkaz:

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 V prostředí Windows PowerShell můžete zadat příkaz přímo:

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> Vzhledem k tomu, že mnoho tříd v WIF 3,5 a WIF 4,5 sdílí stejné názvy, při použití WIF 3,5 a WIF 4,5 společně, nezapomeňte buď použít plně kvalifikované názvy tříd, nebo použít aliasy oboru názvů k rozlišení mezi třídami v WIF 3,5 a WIF 4,5.

## <a name="see-also"></a>Viz také:

- [Schéma konfigurace WIF](../configure-apps/file-schema/windows-identity-foundation/index.md)
- [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Novinky ve Windows Workflow Foundation 4.5](whats-new-in-wif.md)
- [Nástroj Identita a přístup pro Visual Studio 2012](identity-and-access-tool-for-vs.md)
