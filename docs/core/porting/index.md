---
title: Port od .NET Framework do .NET Core
description: Pochopení procesu přenosu a zjišťování nástrojů, které můžete najít užitečné při přenosu .NET Framework projektu do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937324"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Přehled přenosů z .NET Framework do .NET Core

Je možné, že máte kód, který se v současnosti spouští na .NET Framework, které vás zajímá o přenos do .NET Core. Tento článek obsahuje:

* Přehled procesu přenosu.
* Seznam nástrojů, které můžete najít užitečné při přenosu kódu do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenosu

Při přenosu projektu do .NET Core doporučujeme použít následující postup:

1. Přecílíte na všechny projekty, které chcete přenést na cílovou .NET Framework 4.7.2 nebo vyšší.

   Tento krok zajistí, že můžete použít alternativy rozhraní API pro cíle specifické pro .NET Framework, když .NET Core nepodporuje konkrétní rozhraní API.

2. Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) můžete analyzovat vaše sestavení a zjistit, jestli jsou přenosné do .NET Core.

   Nástroj Analyzátor přenositelnosti API analyzuje kompilovaná sestavení a generuje sestavu. Tato sestava zobrazuje souhrn přenositelnosti na vysoké úrovni a rozdělení každého rozhraní API, které používáte, není k dispozici v rozhraní .NET Core.

3. Nainstalujte do svých projektů [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) a Identifikujte rozhraní API, která vyvolávají <xref:System.PlatformNotSupportedException> na některých platformách a nějaké jiné potenciální problémy s kompatibilitou.

   Tento nástroj je podobný analyzátoru přenositelnosti, ale místo analýzy, jestli se kód může sestavovat v .NET Core, analyzuje, jestli používáte rozhraní API způsobem, který v době běhu vyvolá <xref:System.PlatformNotSupportedException>. I když se nejedná o běžný postup, Pokud přesouváte z .NET Framework 4.7.2 nebo vyšší, je dobré ho kontrolovat. Další informace o rozhraních API, která vyvolávají výjimky v rozhraní .NET Core, najdete v tématu [rozhraní API, která vždy vyvolají výjimky v rozhraní .NET Core](../compatibility/unsupported-apis.md).

4. Převeďte všechny své `packages.config` závislosti na formát [PackageReference](/nuget/consume-packages/package-references-in-project-files) pomocí nástroje pro [převod v aplikaci Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Tento krok zahrnuje převod závislostí ze staršího formátu `packages.config`. `packages.config` nefunguje v rozhraní .NET Core, proto je tento převod nutný, pokud máte závislosti balíčku.

5. Vytvořte nové projekty pro .NET Core a zkopírujte přes zdrojové soubory nebo se pokuste převést existující soubor projektu pomocí nástroje.

   .NET Core používá zjednodušený (a odlišný) [Formát souboru projektu](../tools/csproj.md) než .NET Framework. Aby bylo možné pokračovat, budete muset soubory projektu převést do tohoto formátu.

6. Port vašeho testovacího kódu.

   Vzhledem k tomu, že přenos do .NET Core je taková významná změna vašeho základu kódu, důrazně doporučujeme přenést testovací projekty, abyste mohli spustit testy během přenosu kódu. MSTest, xUnit a NUnit všechny fungují na .NET Core.

Kromě toho se můžete pokusit přenést menší řešení nebo jednotlivé projekty v jedné operaci do formátu souboru projektu .NET Core pomocí nástroje [dotnet try-Convert](https://github.com/dotnet/try-convert) . `dotnet try-convert` není zaručená práce pro všechny vaše projekty a může způsobit drobné změny v chování, které jste v závislosti na. Použijte ho jako _výchozí bod_ , který automatizuje základní věci, které je možné automatizovat. Není zaručené řešení pro migraci projektu.

## <a name="next-steps"></a>Další kroky

>[!div class="nextstepaction"]
>[Analyzovat závislosti](third-party-deps.md)
