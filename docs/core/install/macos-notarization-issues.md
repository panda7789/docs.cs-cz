---
title: Práce s macOS Catalina Notarization
description: Jak zpracovat notářizaci a problémy s certifikáty s macOS při instalaci runtime .NET Core, Sady SDK a aplikací vytvořených pomocí .NET Core.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146746"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Notarization a dopad na stahování a projekty .NET Core

Počínaje macOS Catalina (verze 10.15), veškerý software vytvořený po červnu 1, 2019 a distribuovaný s ID vývojáře, musí být notářsky.Rúzy s MacOS Catalina (verze 10.15), veškerý software postavený po 1. Tento požadavek se vztahuje na modul runtime .NET Core, sadku .NET Core SDK a software vytvořený pomocí .NET Core. Tento článek popisuje běžné scénáře, kterým můžete čelit s notazací .NET Core a macOS.

## <a name="installing-net-core"></a>Instalace jádra rozhraní .NET

Instalační programy pro .NET Core (runtime a SDK) verze 3.1, 3.0 a 2.1 byly notářsky oznamovány od 18. Předchozí vydané verze nejsou notářsky oslněny. Nenotářskou verzi rozhraní .NET Core můžete nainstalovat ručně tak, že nejprve `sudo installer` stáhnete instalační program a potom použijete příkaz. Další informace najdete [v tématu Stažení a ruční instalace macOS](sdk.md?pivots=os-macos#download-and-manually-install).

Počínaje následujícími verzemi jsou instalátory .NET Core notářsky ozářené:

- .NET Core Runtime
  - 2.1.16
  - 3.0.3
  - 3.1.2

- Sada .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost je ve výchozím nastavení zakázán

Ve výchozím nastavení nenotalizované verze sady .NET Core SDK 3.0 a vyšší vytvářejí nativní spustitelný soubor Mach-O (označovaný jako **appHost),** když váš projekt zkompiluje, publikuje nebo je spuštěn. Tento spustitelný soubor je pohodlný způsob, jak spustit aplikaci. V opačném případě musí být `dotnet <filename.dll>`aplikace spuštěna spuštěním aplikace . Když je appHost povolen, `dotnet run` příkaz je vyvolán v kontextu appHost. Další informace naleznete [v tématu Kontext appHost](#context-of-the-apphost).

Počínaje notářsky oznamovanými verzemi sady .NET Core SDK 3.0 a vyšší není spustitelný soubor appHost ve výchozím nastavení generován. Generování appHost můžete zapnout [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) pomocí logického nastavení v souboru projektu. Můžete také přepnout appHost `-p:UseAppHost` s parametrem na příkazovém řádku pro konkrétní `dotnet` příkaz, který spustíte:

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

AppHost se vždy vytvoří, když publikujete aplikaci [samostatnou](../deploying/index.md#publish-self-contained).

Další informace o `UseAppHost` nastavení naleznete v [tématu Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Kontext appHost

Když je appHost ve vašem projektu povolen `dotnet run` a pomocí příkazu spustíte aplikaci, aplikace se vyvolá v kontextu appHost a `dotnet` ne výchozího hostitele (výchozí hostitel je příkaz). Pokud je appHost ve vašem `dotnet run` projektu zakázán, příkaz spustí vaši aplikaci v kontextu výchozího hostitele. I když je appHost zakázán, publikování aplikace jako samostatné generuje spustitelný soubor appHost a uživatelé používají tento spustitelný soubor ke spuštění aplikace. Spuštění aplikace `dotnet <filename.dll>` s vyvolá aplikaci s výchozím hostitelem, sdíleným runtime.

Když je vyvolána aplikace používající appHost, oddíl certifikátu, ke kterým má aplikace přístup, se liší od notářsky oznamovaného výchozího hostitele. Pokud vaše aplikace musí přistupovat k certifikátům `dotnet run` nainstalovaným přes výchozí ho hostitele, spusťte aplikaci přímo pomocí příkazu ze souboru projektu nebo pomocí příkazu `dotnet <filename.dll>` spusťte aplikaci přímo.

Další informace o tomto scénáři jsou k dispozici v [části ASP.NET jádra a macOS a certifikáty.](#aspnet-core-and-macos-and-certificates)

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core a macOS a certifikáty

.NET Core poskytuje možnost spravovat certifikáty v řetězci <xref:System.Security.Cryptography.X509Certificates> klíčů macOS s třídou. Přístup k řetězci klíčů macOS používá identitu aplikací jako primární klíč při rozhodování o tom, který oddíl je třeba zvážit. Například nepodepsané aplikace ukládají tajné klíče v nepodepsaném oddílu, ale podepsané aplikace ukládají své tajné klíče v oddílech pouze k nim. Zdroj spuštění, který vyvolá vaše aplikace rozhodne, který oddíl použít.

.NET Core poskytuje tři zdroje spuštění: [appHost](#apphost-is-disabled-by-default), výchozí hostitel `dotnet` (příkaz) a vlastní hostitel. Každý model spuštění může mít různé identity, podepsané nebo nepodepsané a má přístup k různým oddílům v rámci řetězce klíčů. Certifikáty importované jedním režimem nemusí být přístupné z jiného režimu. Například notářsky oznamované verze .NET Core mají výchozího hostitele, který je podepsán. Certifikáty jsou importovány do zabezpečeného oddílu na základě jeho identity. Tyto certifikáty nejsou přístupné z generované aplikaceHost, protože appHost je nepodepsaný.

Jiný příklad ve výchozím nastavení ASP.NET Core importuje výchozí certifikát SSL prostřednictvím výchozího hostitele. ASP.NET Základní aplikace, které používají appHost nebude mít přístup k tomuto certifikátu a obdrží chybu, když .NET Core zjistí, že certifikát není přístupný. Chybová zpráva obsahuje pokyny k vyřešení tohoto problému.

Pokud je vyžadováno sdílení certifikátů, macOS poskytuje možnosti konfigurace s `security` nástrojem.

Další informace o řešení problémů s certifikáty ASP.NET základní informace naleznete [v tématu Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Výchozí nároky

Výchozí hostitel rozhraní .NET `dotnet` Core (příkaz) má sadu výchozích nároků. Tyto nároky jsou vyžadovány pro správné fungování .NET Core. Je možné, že vaše aplikace může potřebovat další nároky, v takovém případě budete muset generovat a používat [appHost](#apphost-is-disabled-by-default) a pak přidat potřebné nároky místně.

Výchozí sada nároků pro jádro .NET:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notáži aplikace .NET Core

Pokud chcete, aby vaše aplikace běžela na macOS Catalina (verze 10.15) nebo vyšší, budete chtít svou aplikaci notářsky ověřit. AppHost, který odešlete s žádostí o notářskou insukci, by měl být používán s alespoň stejnými [výchozími nároky](#default-entitlements) pro .NET Core.

## <a name="next-steps"></a>Další kroky

- [.NET Základní závislosti a požadavky](dependencies.md).
- [Nainstalujte sadu .NET Core SDK](sdk.md).
- [Instalace rozhraní .NET Core Runtime](runtime.md)
