---
title: Práce s macOS Catalina notarization
description: Jak zvládnout notarization a problémy s certifikáty pomocí macOS při instalaci modulu runtime .NET Core, sady SDK a aplikací vytvořených pomocí .NET Core
author: adegeo
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: a7741727ad46216ebd9936515d8af29b6d7049c2
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656524"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina notarization a dopad na stažení a projekty .NET Core

Od macOS Catalina (verze 10,15) je nutné, aby byl veškerý software sestavený od 1. června 2019 a distribuován s ID vývojáře notarized. Tento požadavek se vztahuje na modul runtime .NET Core, .NET Core SDK a software vytvořený pomocí .NET Core. Tento článek popisuje běžné scénáře, se kterými se můžete setkat s .NET Core a macOS Notarization.

## <a name="installing-net-core"></a>Instalace .NET Core

Instalační programy pro .NET Core (běhové i sady SDK) verze 3,1, 3,0 a 2,1 byly notarized od 18. února 2020. Předchozí vydané verze nejsou notarized. Nenotarized verzi rozhraní .NET Core můžete nainstalovat ručně, a to tak, že nejprve stáhnete instalační program a potom použijete `sudo installer` příkaz. Další informace najdete v tématu [Stažení a ruční instalace pro MacOS](sdk.md?pivots=os-macos#download-and-manually-install).

Od následujících verzí jsou instalační programy .NET Core notarized:

- .NET Core Runtime
  - 2.1.16
  - 3.0.3
  - 3.1.2

- Sada .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost je ve výchozím nastavení zakázaná.

Ve výchozím nastavení nenotarized verze .NET Core SDK 3,0 a vyšší mají za následek, že se při kompilaci projektu, publikování nebo spuštění spustí nativní spustitelný soubor strojového souboru (označovaný jako **appHost**). Tento spustitelný soubor je pohodlný způsob, jak aplikaci spustit. V opačném případě musí být aplikace spuštěná `dotnet <filename.dll>` . Když je povolený appHost, `dotnet run` příkaz se vyvolá v kontextu appHost. Další informace najdete v tématu [kontext appHost](#context-of-the-apphost).

Počínaje verzí notarized .NET Core SDK 3,0 a vyšší se ve výchozím nastavení negeneruje spustitelný soubor appHost. Můžete zapnout generování appHost s [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) nastavením Boolean v souboru projektu. Můžete také přepnout appHost s `-p:UseAppHost` parametrem na příkazovém řádku pro konkrétní `dotnet` příkaz, který spustíte:

- Soubor projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr příkazového řádku

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

AppHost se vždy vytvoří při publikování [vlastní](../deploying/index.md#publish-self-contained)aplikace.

Další informace o tomto `UseAppHost` nastavení najdete v tématu [vlastnosti MSBuild pro Microsoft. NET. SDK](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Kontext appHost

Když je v projektu povolený appHost a použijete `dotnet run` příkaz ke spuštění vaší aplikace, vyvolá se aplikace v kontextu appHost a ne jako výchozí hostitel (výchozí hostitel je `dotnet` příkaz). Pokud je appHost v projektu zakázaný, `dotnet run` příkaz spustí vaši aplikaci v kontextu výchozího hostitele. I když je appHost zakázaný, publikování aplikace jako samostatné vygeneruje spustitelný soubor appHost a uživatelé tento spustitelný soubor použijí ke spuštění vaší aplikace. Spuštění vaší aplikace pomocí `dotnet <filename.dll>` vyvolá aplikaci s výchozím hostitelem, sdíleným modulem runtime.

Po vyvolání aplikace používající appHost se oddíl certifikátu, ke kterému se aplikace přistupovala, liší od výchozího hostitele notarized. Pokud vaše aplikace musí přistupovat k certifikátům nainstalovaným prostřednictvím výchozího hostitele, použijte `dotnet run` příkaz ke spuštění aplikace ze souboru projektu nebo použijte `dotnet <filename.dll>` příkaz ke spuštění aplikace přímo.

Další informace o tomto scénáři najdete v části [ASP.NET Core a MacOS a certifikáty](#aspnet-core-and-macos-and-certificates) .

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core a macOS a certifikáty

.NET Core poskytuje možnost spravovat certifikáty v řetězci klíčů macOS s <xref:System.Security.Cryptography.X509Certificates> třídou. Přístup k řetězci macOS používá při rozhodování, který oddíl má být považován za primární klíč, identitu aplikace. Nepodepsané aplikace například ukládají tajné klíče do nepodepsaného oddílu, ale podepsané aplikace ukládají jejich tajné klíče pouze do oddílů, ke kterým mají přístup. Zdroj spuštění, který vyvolá aplikaci, rozhoduje o tom, který oddíl se má použít.

.NET Core poskytuje tři zdroje spuštění: [appHost](#apphost-is-disabled-by-default), výchozí hostitel ( `dotnet` příkaz) a vlastní hostitel. Každý model spuštění může mít různé identity, buď podepsané, nebo bez znaménka, a má přístup k různým oddílům v řetězci klíčů. Certifikáty naimportované v jednom režimu nemusí být dostupné z jiné. Například verze notarized .NET Core mají výchozího hostitele, který je podepsaný. Certifikáty se importují do zabezpečeného oddílu na základě jeho identity. Tyto certifikáty nejsou přístupné z vygenerovaných appHost, protože appHost je bez znaménka.

Ve výchozím nastavení například ASP.NET Core importuje výchozí certifikát SSL prostřednictvím výchozího hostitele. ASP.NET Core aplikace, které používají appHost, nebudou mít přístup k tomuto certifikátu a zobrazí se chyba, když .NET Core zjistí, že certifikát není přístupný. Chybová zpráva poskytuje pokyny k vyřešení tohoto problému.

Pokud je vyžadováno sdílení certifikátů, macOS poskytuje možnosti konfigurace pomocí `security` nástroje.

Další informace o řešení problémů s certifikátem ASP.NET Core najdete v tématu vystavení [protokolu HTTPS v ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Výchozí nároky

Výchozí hostitel .NET Core ( `dotnet` příkaz) má sadu výchozích nároků. Tato oprávnění se vyžadují ke správnému fungování .NET Core. Je možné, že vaše aplikace bude potřebovat další nároky. v takovém případě budete muset vygenerovat a používat [appHost](#apphost-is-disabled-by-default) a potom přidat potřebná oprávnění místně.

Výchozí sada nároků pro .NET Core:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notarize aplikace .NET Core

Pokud chcete, aby vaše aplikace běžela na macOS Catalina (verze 10,15) nebo vyšší, budete chtít notarize aplikaci. AppHost, které odesíláte s vaší aplikací pro notarization, by se měla použít s alespoň stejnými [výchozími nároky](#default-entitlements) pro .NET Core.

## <a name="next-steps"></a>Další kroky

- [Závislosti a požadavky rozhraní .NET Core](macos.md#dependencies).
- [Nainstalujte modul runtime .NET Core a sadu SDK](macos.md).
