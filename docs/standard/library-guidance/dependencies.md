---
title: Závislosti a knihovny .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet v knihovnách .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731475"
---
# <a name="dependencies"></a>Závislosti

Primární způsob přidávání závislostí do knihovny .NET odkazuje na balíčky NuGet. Odkazy na balíčky NuGet umožňují rychle znovu použít a využít již napsané funkce, ale jsou běžným zdrojem tření pro vývojáře rozhraní .NET. Správná správa závislostí je důležitá, aby se zabránilo změnám v jiných knihovnách .NET v porušení knihovny .NET a naopak!

## <a name="diamond-dependencies"></a>Diamantové závislosti

Je běžné situace pro projekt .NET mít více verzí balíčku ve svém stromu závislostí. Například aplikace závisí na dvou balíčcích NuGet, z nichž každý závisí na různých verzích stejného balíčku. V grafu závislostí aplikace nyní existuje závislost na kosočtverci.

![Závislost na kosočtverci](./media/dependencies/diamond-dependency.png "Závislost na kosočtverci")

V době sestavení NuGet analyzuje všechny balíčky, které závisí na projektu, včetně závislostí závislostí. Při zjištění více verzí balíčku jsou vyhodnocovány pravidla vybrat jeden. Sjednocení balíčků je nezbytné, protože spuštění souběžných verzí sestavení ve stejné aplikaci je problematické v rozhraní .NET.

Většina diamantové závislosti jsou snadno přeložit; mohou však za určitých okolností způsobit problémy:

1. **Konfliktní odkazy na balíček NuGet** brání vyřešení verze během obnovení balíčku.
2. **Narušující změny mezi verzemi** způsobit chyby a výjimky za běhu.
3. **Sestavení balíčku je silné s názvem**, verze sestavení změněna a aplikace je spuštěna v rozhraní .NET Framework. Jsou vyžadována přesměrování vazby sestavení.

Není možné vědět, jaké balíčky budou použity vedle své vlastní. Dobrým způsobem, jak snížit pravděpodobnost, že závislost na kosobru sdiamantové mincovní zařízení rozlomí vaši knihovnu, je minimalizovat počet balíčků, na kterých jste závislí.

✔️ do zkontrolujte knihovnu .NET pro zbytečné závislosti.

## <a name="nuget-dependency-version-ranges"></a>Rozsahy verzí závislostí NuGet

Odkaz na balíček určuje rozsah platných balíčků, které umožňuje. Referenční verze balíčku v souboru projektu je obvykle minimální verze a neexistuje žádné maximum.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Pravidla, která NuGet používá při řešení závislostí jsou [složité](/nuget/consume-packages/dependency-resolution), ale NuGet vždy hledá nejnižší použitelnou verzi. NuGet upřednostňuje nejnižší použitelnou verzi před použitím nejvyšší dostupné, protože nejnižší bude mít nejmenší problémy s kompatibilitou.

Z důvodu nuget nejnižší použitelné verze pravidlo, není nutné umístit horní verzi nebo přesný rozsah na odkazy na balíček, aby se zabránilo získání nejnovější verze. NuGet se již snaží najít nejnižší, nejvíce kompatibilní verze pro vás.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Horní verze omezení způsobí NuGet nezdaří, pokud dojde ke konfliktu. Například jedna knihovna přijímá přesně 1.0, zatímco jiná knihovna vyžaduje 2.0 nebo vyšší. Při porušení změny mohou být zavedeny ve verzi 2.0, přísné nebo horní limit verze závislost zaručuje chybu.

![Konflikt závislosti na diamantech](./media/dependencies/diamond-dependency-conflict.png "Konflikt závislosti na diamantech")

❌Nemají Odkazy na balíček NuGet bez minimální verze.

❌VYHNĚTE se NuGet odkazy na balíček, které vyžadují přesnou verzi.

❌VYHNĚTE se Odkazy na balíček NuGet s horním limitem verze.

## <a name="nuget-shared-source-packages"></a>Balíčky sdíleného zdroje NuGet

Jedním ze způsobů, jak snížit externí NuGet balíček závislostí je odkazovat na sdílené zdrojové balíčky. Sdílený zdrojový balíček obsahuje [soubory zdrojového kódu,](/nuget/reference/nuspec#including-content-files) které jsou zahrnuty v projektu při odkazování. Vzhledem k tomu, že jste právě včetně souborů zdrojového kódu, které jsou kompilovány se zbytkem projektu, neexistuje žádná externí závislost a šance na konflikt.

Sdílené zdrojové balíčky jsou skvělé pro zahrnutí malých částí funkcí. Například sdílený zdrojový balíček pomocných metod pro volání HTTP.

![Sdílený zdrojový balíček](./media/dependencies/shared-source-package.png "Sdílený zdrojový balíček")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Projekt sdíleného zdroje](./media/dependencies/shared-source-project.png "Projekt sdíleného zdroje")

Sdílené zdrojové balíčky mají určitá omezení. Mohou být odkazovány `PackageReference`pouze na `packages.config` , takže starší projekty jsou vyloučeny. Sdílené zdrojové balíčky jsou použitelné pouze pro projekty se stejným typem jazyka. Z důvodu těchto omezení sdílené zdrojové balíčky se nejlépe používají ke sdílení funkcí v rámci projektu s otevřeným zdrojovým kódem.

✔️ zvažte odkazování na sdílené zdrojové balíčky pro malé, interní části funkcí.

✔️ zvažte vytvoření balíčku sdílený zdrojový balíček, pokud poskytuje malé, vnitřní části funkcí.

✔️ do odkaz sdílené `PrivateAssets="All"`zdrojové balíčky s .

> Toto nastavení říká NuGet balíček je pouze pro použití v době vývoje a by neměly být vystaveny jako veřejné závislosti.

❌Nemáte sdílené typy zdrojových balíčků ve veřejném rozhraní API.

> Sdílené typy zdrojů jsou kompilovány do referenčního sestavení a nelze je vyměňovat přes hranice sestavení. Například typ sdíleného `IRepository` zdroje v jednom projektu je samostatný typ `IRepository` ze stejného sdíleného zdroje v jiném projektu. Typy ve sdílených zdrojových balíčcích by měly mít `internal` viditelnost.

❌NEPublikujte sdílené zdrojové balíčky, které mají NuGet.org.

> Sdílené zdrojové balíčky obsahují zdrojový kód a mohou být používány pouze projekty se stejným typem jazyka. Například balíček sdíleného zdroje Jazyka C# nelze použít aplikací F#.
>
> Publikovat sdílené zdrojové balíčky do [místního informačního kanálu nebo MyGet](./publish-nuget-package.md) využívat interně v rámci projektu.

>[!div class="step-by-step"]
>[Předchozí](nuget.md)
>[další](sourcelink.md)
