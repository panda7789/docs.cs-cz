---
title: Závislosti a knihoven .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0cd00ff36ad52bc46769ca1793b9efd02db14da1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644268"
---
# <a name="dependencies"></a>Závislosti

Primární způsob, jak přidat závislosti do knihovny .NET odkazuje na balíčky NuGet. Odkazy na balíčky NuGet umožňují rychle opakovaně používat a využít už písemné funkce, ale jsou běžné příčiny případná problémová místa pro vývojáře na platformě .NET. Správně Správa závislostí je důležité zabránit změnám v jiných knihovnách .NET z nejnovější knihovny .NET a naopak.

## <a name="diamond-dependencies"></a>Závislosti kosočtverec

Je běžné situace pro projekt .NET pro více verzí balíčku v jeho strom závislostí. Například aplikace závisí na dva balíčky NuGet, z nichž každý závisí na různé verze stejného balíčku. Závislost kosočtverce nyní existuje v grafu závislostí aplikace.

![Diamond závislost](./media/dependencies/diamond-dependency.png "Diamond závislostí")

V okamžiku sestavení NuGet analyzuje všech balíčků projektu, na kterých závisí, včetně závislostí závislosti. Když se zjistí více verzí balíčku, pravidla se vyhodnocují vybrat jednu. Sjednotit balíčků je nezbytné, protože spuštěná verze sestavení vedle sebe ve stejné aplikaci jen těžko v rozhraní .NET.

Většina kosočtverce závislosti jsou snadno vyřešit; v některých případech však může vytvořit problémy:

1. **Konfliktní odkazy na balíčky NuGet** zabránit se přeloží během obnovení balíčku verze.
2. **Rozbíjející změny mezi verzí** způsobovat chyby a výjimky za běhu.
3. **Balíček sestavení silně pojmenováno**změně verze sestavení a spuštění aplikace v rozhraní .NET Framework. Přesměrování vazby sestavení jsou povinné.

Není možné zjistit, jaké balíčky budou používat souběžně s vlastními. Dobrým způsobem, jak snížit pravděpodobnost, že kosočtverce závislosti zásadní knihovny je minimalizovat počet balíčků, které nejvíc potřebujete.

**PROVEĎTE ✔️** zkontrolujte vaše knihovna .NET pro nepotřebné závislosti.

## <a name="nuget-dependency-version-ranges"></a>Rozsahů verzí závislostí NuGet

Odkaz na balíček určuje rozsah platný balíčky, které umožňuje. Obvykle referenční verze balíčku v souboru projektu je minimální verze a neexistuje žádná maximální.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Jsou pravidla, která používá NuGet při řešení závislostí [komplexní](/nuget/consume-packages/dependency-resolution), ale NuGet vždycky hledá na nejnižší příslušné verzi. NuGet upřednostňuje nejnižší použitelná verze oproti použití nejvyšší dostupná, protože nejnižší bude mít nejnižší problémy s kompatibilitou.

Z důvodu nejnižší pravidlo použít verze NuGet není potřeba umístit horní verzi nebo přesně rozsah na odkazy na balíček, aby se zabránilo načtení nejnovější verze. NuGet již pokusí najít verzi nejnižší, nejkompatibilnější za vás.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Verze horní omezení způsobí, že správci balíčků NuGet selhat, pokud dojde ke konfliktu. Například jedna knihovna přijímá přesně 1,0, zatímco jiné knihovny vyžaduje 2.0 nebo vyšší. Zatímco rozbíjející změny v může zavedly ve verzi 2.0, závislost verze strict nebo horní mez zaručuje chybu.

![Diamond závislost konflikt](./media/dependencies/diamond-dependency-conflict.png "Diamond konflikt závislostí")

**❌ NEPODPORUJÍ** mají odkazy na balíčky NuGet se žádná minimální verze.

**❌ Nepoužívejte** odkazy na balíčky NuGet, které vyžadují přesnou verzi.

**❌ Nepoužívejte** odkazy na balíček NuGet s verzí horní mez.

## <a name="nuget-shared-source-packages"></a>Balíčky NuGet, které jsou sdílené zdroje

Jedním ze způsobů ke snížení externí závislosti balíčků NuGet je odkazují na sdílené zdroje balíčků. Sdílený zdrojový balíček obsahuje [souborů zdrojového kódu](/nuget/reference/nuspec#including-content-files) , které jsou součástí projektu při odkazování. Protože jste právě včetně soubory zdrojového kódu, které jsou kompilovány s využitím zbytku projektu, neexistuje žádné externí závislosti a pravděpodobnost konfliktu.

Sdílený zdroj, které balíčky se skvěle hodí k včetně malé funkce. Například sdílené zdroje balíčku z metody helper pro volání HTTP.

![Sdílený zdroj balíčku](./media/dependencies/shared-source-package.png "sdílené zdroje balíčku")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Sdílený zdroj projektu](./media/dependencies/shared-source-project.png "sdílený zdrojový projekt")

Sdílený zdroj balíčků mají určitá omezení. Se může odkazovat jen `PackageReference`, tak starší `packages.config` projekty jsou vyloučeny. Sdílený zdroj balíčků jsou také pouze použitelný pro projekty se stejným typem jazyka. Z důvodu tato omezení jsou nejvhodnější sdílené zdroje balíčků ke sdílení funkcí v rámci projektu aplikace open source.

**✔️ ZVAŽTE** odkazování na sdílené zdroje balíčků pro malé a interní funkční součásti.

**✔️ ZVAŽTE** provádění vašeho balíčku sdílené zdroje balíčku pokud poskytuje malé, interní funkční součásti.

**PROVEĎTE ✔️** odkazují na sdílené zdroje balíčků s `PrivateAssets="All"`.

> Toto nastavení určuje balíček NuGet je pouze pro použití při vývoji a by neměly být vystaveny jako veřejné závislost.

**❌ NEPODPORUJÍ** být sdílených typů zdroje balíčku ve veřejném rozhraní API.

> Sdílený zdroj typy jsou kompilovány do odkazující sestavení a nemůže se vyměňují přes hranice sestavení. Například sdílené zdroje `IRepository` typ v jednom projektu je samostatný typ ze stejného sdíleného zdroje `IRepository` v jiném projektu. Typy v balíčcích sdílené zdroje by měly mít `internal` viditelnost.

**❌ NEPODPORUJÍ** publikování sdílené zdroje balíčků na NuGet.org.

> Sdílený zdroj balíčky obsahují zdrojový kód a jde použít jenom projekty se stejným typem jazyka. Například C# sdílené zdroje balíčku nelze použít pro F# aplikace.
>
> Publikovat balíčky sdílené zdroje, které mají [místní informační kanál či MyGet](./publish-nuget-package.md) využívat interně v rámci svého projektu.

>[!div class="step-by-step"]
>[Předchozí](nuget.md)
>[další](sourcelink.md)
