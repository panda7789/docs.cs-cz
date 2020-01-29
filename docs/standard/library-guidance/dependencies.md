---
title: Závislosti a knihovny .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet v knihovnách .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731475"
---
# <a name="dependencies"></a>Závislosti

Hlavním způsobem přidání závislostí do knihovny .NET je odkazování na balíčky NuGet. Odkazy na balíček NuGet vám umožní rychle znovu využít a využívat už napsané funkce, ale jsou to společný zdroj tření pro vývojáře na platformě .NET. Správná Správa závislostí je důležité, aby nedošlo ke změnám v jiných knihovnách .NET proti narušení vaší knihovny .NET a naopak.

## <a name="diamond-dependencies"></a>Kosočtvercové závislosti

V případě, že projekt .NET má ve stromu závislostí více verzí balíčku, je běžné situaci. Například aplikace závisí na dvou balíčcích NuGet, přičemž každý z nich závisí na různých verzích stejného balíčku. V grafu závislostí aplikace teď existuje závislost kosočtverce.

![Kosočtverec – závislost](./media/dependencies/diamond-dependency.png "Kosočtverec – závislost")

V době sestavení NuGet analyzuje všechny balíčky, na kterých projekt závisí, včetně závislostí závislostí. Při zjištění více verzí balíčku se pravidla vyhodnotí, aby se vybrala jedna. Sjednocení balíčků je nezbytné, protože spuštěné souběžné verze sestavení ve stejné aplikaci jsou v rozhraní .NET problematické.

Většinu diamantových závislostí lze snadno vyřešit. můžou se ale v určitých případech vytvářet problémy:

1. **Konfliktní odkazy na balíčky NuGet** brání v vyřešení verze během obnovování balíčku.
2. **Narušením změn mezi verzemi** dojde k chybám a výjimkám za běhu.
3. **Sestavení balíčku má silný název**, verze sestavení se změnila a aplikace je spuštěná na .NET Framework. Přesměrování vazby sestavení jsou povinná.

Není možné zjistit, jaké balíčky se budou používat společně s vašimi vlastními. Dobrým způsobem, jak snížit pravděpodobnost přerušení vaší knihovny, je minimalizovat počet balíčků, na kterých jste závislí.

✔️ Projděte si knihovnu .NET, abyste měli zbytečné závislosti.

## <a name="nuget-dependency-version-ranges"></a>Rozsahy verzí závislosti NuGet

Odkaz na balíček určuje rozsah platných balíčků, které umožňuje. Obvykle je referenční verze balíčku v souboru projektu minimální verze a neexistuje žádná maximální hodnota.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Pravidla, která nástroj NuGet používá při řešení závislostí, jsou [složitá](/nuget/consume-packages/dependency-resolution), ale NuGet vždy vyhledává nejnižší platnou verzi. NuGet upřednostňuje nejnižší použitelnou verzi přes nejvyšší dostupný, protože nejnižší bude mít minimálně problémy s kompatibilitou.

Vzhledem k tomu, že pravidlo pro nejnižší verzi NuGetu splňuje, není nutné při odkazech na balíček umístit horní nebo přesný rozsah, aby se předešlo získání nejnovější verze. NuGet se už snaží najít nejnižší, nejvíce kompatibilní verzi.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Omezení horní verze způsobí selhání NuGet v případě konfliktu. Například jedna knihovna akceptuje přesně 1,0, zatímco jiná knihovna vyžaduje 2,0 nebo vyšší. I když mohou být zásadní změny představené ve verzi 2,0, je zaručena chybná závislost verze striktní nebo horní limit.

![Konflikt závislosti v kosočtverec](./media/dependencies/diamond-dependency-conflict.png "Konflikt závislosti v kosočtverec")

❌ nemáte odkazy na balíček NuGet bez minimální verze.

❌ se vyhnout odkazům na balíček NuGet, které vyžadují přesnou verzi.

❌ se vyhnout odkazům na balíček NuGet s horním limitem verze.

## <a name="nuget-shared-source-packages"></a>Sdílené zdrojové balíčky NuGet

Jedním ze způsobů, jak omezit externí závislosti balíčků NuGet, je odkazování na sdílené zdrojové balíčky. Sdílený zdrojový balíček obsahuje [soubory zdrojového kódu](/nuget/reference/nuspec#including-content-files) , které jsou zahrnuty v projektu, pokud se na něj odkazuje. Vzhledem k tomu, že právě jste zadali soubory zdrojového kódu, které jsou kompilovány se zbytkem projektu, neexistuje žádná externí závislost a šance na konflikt.

Sdílené zdrojové balíčky jsou skvělé pro zahrnutí malých kousků funkcí. Například sdílený zdrojový balíček pomocných metod pro vytváření volání HTTP.

![Sdílený zdrojový balíček](./media/dependencies/shared-source-package.png "Sdílený zdrojový balíček")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Sdílený zdrojový projekt](./media/dependencies/shared-source-project.png "Sdílený zdrojový projekt")

Sdílené zdrojové balíčky mají určitá omezení. Můžou na ně odkazovat jenom `PackageReference`, aby se vyloučily starší `packages.config` projekty. Sdílené zdrojové balíčky jsou také použitelné pouze v projektech se stejným typem jazyka. Z důvodu těchto omezení jsou sdílené zdrojové balíčky nejlépe používány pro sdílení funkcí v rámci open source projektu.

✔️ Zvažte odkazování na sdílené zdrojové balíčky pro malé, interní funkce.

✔️ Zvažte vytvoření balíčku sdíleného zdrojového kódu, pokud poskytuje malé, interní funkce.

✔️ odkazují na sdílené zdrojové balíčky pomocí `PrivateAssets="All"`.

> Toto nastavení říká NuGet, že balíček se má použít jenom v době vývoje a neměl by být vystavený jako veřejná závislost.

ve veřejném rozhraní API není ❌ sdílené zdrojové typy balíčků.

> Sdílené zdrojové typy jsou kompilovány do odkazujícího sestavení a nelze je vyměňovat přes hranice sestavení. Například typ Shared-Source `IRepository` v jednom projektu je samostatný typ ze stejného `IRepository` Shared Source v jiném projektu. Typy ve sdílených zdrojových balíčcích by měly mít `internal` viditelnost.

❌ nepublikujte sdílené zdrojové balíčky do NuGet.org.

> Sdílené zdrojové balíčky obsahují zdrojový kód a mohou být použity pouze v projektech se stejným typem jazyka. Například C# sdílený zdrojový balíček nemůže používat F# aplikace.
>
> Publikujte sdílené zdrojové balíčky do [místního kanálu nebo MyGet](./publish-nuget-package.md) , aby je bylo možné interně spotřebovat ve vašem projektu.

>[!div class="step-by-step"]
>[Předchozí](nuget.md)
>[Další](sourcelink.md)
