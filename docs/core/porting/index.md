---
title: Kód portu z .NET Framework do .NET Core
description: Pochopení procesu přenosu a zjišťování nástrojů, které můžete najít užitečné při přenosu .NET Framework projektu do .NET Core.
author: cartermp
ms.date: 09/13/2019
ms.custom: seodec18
ms.openlocfilehash: c349f7df3726e7a9814e5ad5e738742ab1bb9ff8
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522985"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Portování kódu z .NET Framework do .NET Core

Pokud máte kód, který běží na .NET Framework, může to být tím, že zajímáte i svůj kód v .NET Core. Tady je přehled procesu přenosu a seznam nástrojů, které můžete najít užitečné při přenosu kódu do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenosu

To je proces, který doporučujeme provést při přenosu projektu do .NET Core. Jednotlivé kroky tohoto procesu jsou podrobněji popsány v dalších článcích.

1. Identifikujte a zaregistrujte závislosti třetích stran.

   Tento krok zahrnuje vysvětlení toho, co jsou závislosti jiných výrobců závislé na tom, jak zjistit, jestli se také spouští na .NET Core, a kroky, které můžete provést, pokud ne. Také se zabývá tím, jak můžete migrovat závislosti do formátu [PackageReference](/nuget/consume-packages/package-references-in-project-files) , který se používá v .NET Core.

2. Přecílíte na všechny projekty, které chcete přenést, aby bylo možné cílit na .NET Framework 4.7.2 nebo vyšší.

   Tento krok zajistí, že můžete použít alternativy rozhraní API pro cíle specifické pro .NET Framework, když .NET Core nepodporuje konkrétní rozhraní API.

3. Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) můžete analyzovat vaše sestavení a vyvíjet plán na základě jeho výsledků.

   Nástroj Analyzátor přenositelnosti rozhraní API analyzuje vaše kompilovaná sestavení a vygeneruje sestavu, která zobrazuje souhrn přenositelnosti na vysoké úrovni a rozpis každého rozhraní API, které používáte, není k dispozici na cílené veřejné platformě .NET Core. Tuto sestavu můžete použít spolu s analýzou základu kódu k vytvoření plánu pro způsob, jakým budete svůj kód portovat.

4. Jakmile budete mít soubor projektu převedený na cílovou verzi .NET Core, můžete použít [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) Roslyn založený k identifikaci rozhraní <xref:System.PlatformNotSupportedException> API na některých platformách a některé jiné potenciální problémy s kompatibilitou.

5. Port kódu testů.

   Vzhledem k tomu, že přenos do .NET Core je podstatnou změnou základu kódu, důrazně doporučujeme, abyste si nadostali své testy, abyste mohli spouštět testy během přenosu kódu. MSTest, xUnit a NUnit podporují .NET Core.

6. Proveďte svůj plán pro přenos.

Následující seznam obsahuje nástroje, které může být užitečné použít během procesu přenosu:

- Analyzátor přenositelnosti .NET – [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), nástroj, který může generovat sestavu způsobu, jakým je přenos kódu mezi .NET Framework a vaší cílovou platformou .NET Core. Sestava obsahuje rozpis sestavení podle sestavení typu a chybějící rozhraní API na cílové platformě .NET Core. Další informace najdete v tématu [analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md). Před zahájením přenosu doporučujeme spustit nástroj Analyzátor přenositelnosti .NET, protože vám pomůže identifikovat mezery v chybějících rozhraních API na konkrétní cílené veřejné ploše platformy .NET.
- Rozhraní .NET API Analyzer – analyzátor Roslyn, který zjišťuje .NET Standard rozhraní API, které vyvolává <xref:System.PlatformNotSupportedException> na některých platformách, detekuje volání zastaralých rozhraní API a zjišťují některá další potenciální rizika kompatibility pro C# rozhraní API na různých platformách. Další informace najdete v tématu [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md). Tento analyzátor je užitečný poté, co jste již vytvořili projekt .NET Core pro identifikaci rozdílů v chování za běhu na různých platformách.
- Zpětné vyhledávání balíčků – [užitečnou webovou službu](https://packagesearch.azurewebsites.net) , která umožňuje vyhledat typ a vyhledat balíčky obsahující tento typ.

Kromě toho se můžete pokusit přenést menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) Tool.

> [!WARNING]
> CsprojToVs2017 je nástroj třetí strany. Není zaručeno, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jsou závislé na. CsprojToVs2017 by měla být použita jako _výchozí bod_ , který automatizuje základní věci, které lze automatizovat. Není zaručené řešení pro migraci formátů souborů projektu.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
