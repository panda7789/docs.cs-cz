---
title: Port z rozhraní .NET Framework do jádra rozhraní .NET
description: Seznamte se s procesem přenosu a objevte nástroje, které mohou být užitečné při přenosu projektu rozhraní .NET Framework do jádra .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937324"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Přehled přenosu z rozhraní .NET Framework do jádra rozhraní .NET

Pravděpodobně máte kód, který je aktuálně spuštěn v rozhraní .NET Framework, který vás zajímá portování na .NET Core. Tento článek obsahuje:

* Přehled procesu přenosu.
* Seznam nástrojů, které mohou být užitečné při přenosu kódu do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenosu

Při přenosu projektu do jádra .NET doporučujeme použít následující postup:

1. Přesměrujte všechny projekty, které chcete portovat, a cílte na rozhraní .NET Framework 4.7.2 nebo vyšší.

   Tento krok zajistí, že můžete použít alternativy rozhraní API pro cíle specifické pro rozhraní .NET Framework, když rozhraní .NET Core nepodporuje konkrétní rozhraní API.

2. Pomocí [nástroje .NET Reability Analyzer](../../standard/analyzers/portability-analyzer.md) analyzujte sestavení a zjistěte, zda jsou přenosná do jádra .NET Core.

   Nástroj API Portability Analyzer analyzuje zkompilovaná sestavení a generuje sestavu. Tato sestava zobrazuje souhrn přenositelnosti na vysoké úrovni a rozpis každého rozhraní API, které používáte, které není k dispozici na NET Core.

3. Nainstalujte [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) do svých <xref:System.PlatformNotSupportedException> projektů k identifikaci rozhraní API, která vyvolána na některých platformách a některé další potenciální problémy s kompatibilitou.

   Tento nástroj je podobný analyzátoru přenositelnosti, ale místo analýzy, pokud kód může stavět na .NET Core, analyzuje, zda používáte rozhraní API způsobem, který vyvolá <xref:System.PlatformNotSupportedException> za běhu. I když to není běžné, pokud přecházíte z rozhraní .NET Framework 4.7.2 nebo vyšší, je vhodné zkontrolovat. Další informace o rozhraní API, která vyvolání výjimek na .NET Core, naleznete v [tématu rozhraní API, která vždy vyvolat výjimky na .NET Core](../compatibility/unsupported-apis.md).

4. Převeďte `packages.config` všechny své závislosti do formátu [PackageReference](/nuget/consume-packages/package-references-in-project-files) pomocí [nástroje pro převod v sadě Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Tento krok zahrnuje převod závislostí `packages.config` ze staršího formátu. `packages.config`nefunguje na .NET Core, takže tento převod je vyžadován, pokud máte závislosti balíčků.

5. Vytvořte nové projekty pro jádro .NET core a zkopírujte je přes zdrojové soubory nebo se pokuste převést existující soubor projektu pomocí nástroje.

   Jádro .NET používá zjednodušený (a jiný) [formát souboru projektu](../tools/csproj.md) než rozhraní .NET Framework. Chcete-li pokračovat, budete muset převést soubory projektu do tohoto formátu.

6. Port testovací kód.

   Vzhledem k tomu, že portování na .NET Core je tak významná změna vašeho základu kódu, důrazně doporučujeme přenést testovací projekty, abyste mohli spouštět testy při přenosu kódu. MSTest, xUnit a NUnit všechny práce na .NET Core.

Kromě toho se můžete pokusit portovat menší řešení nebo jednotlivé projekty v jedné operaci do formátu souboru projektu .NET Core pomocí nástroje [try-convert dotnet.](https://github.com/dotnet/try-convert) `dotnet try-convert`není zaručeno, že pracovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jste závislí na. Použijte jej jako _výchozí bod,_ který automatizuje základní věci, které lze automatizovat. Není to zaručené řešení migrace projektu.

## <a name="next-steps"></a>Další kroky

>[!div class="nextstepaction"]
>[Analýza závislostí](third-party-deps.md)
