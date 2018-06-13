---
title: Správa verze závislosti balíčku pro .NET Core 1.0
description: Další informace o správě verze závislosti balíčku pro knihovny .NET Core a aplikace.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 96d154f045303e32de606475e77ab2e6b4f7bcda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211335"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>Správa verze závislosti balíčku pro .NET Core 1.0

Tento článek popisuje, co potřebujete vědět o verze balíčku pro knihovny .NET Core a aplikace.

## <a name="glossary"></a>Slovníček

**Opravte** -opravě závislosti znamená používáte stejná "rodina" balíčků vydala NuGet pro rozhraní .NET Core 1.0.

**Metapackage** -A NuGet balíček, který představuje sadu balíčků NuGet.

**Ořezávání** -operace odebrání balíčků není závislá na z metapackage.  Toto je něco relevantní pro autory balíček NuGet.  V tématu [snižuje závislosti balíčků s project.json](../deploying/reducing-dependencies.md) Další informace. 

## <a name="fix-your-dependencies-to-net-core-10"></a>Opravte svoje závislosti na .NET Core 1.0

Pokud chcete spolehlivě obnovení balíčků a zápis spolehlivého kódu, je důležité opravili závislostmi verzích balíčky přesouvání spolu s .NET Core 1.0.  To znamená, že každý balíček musí mít jednu verzi s žádné další kvalifikátory.

**Příklady balíčků pevné hodnotě 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Příklady balíčky, které není nastaven na 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Proč této věci?

Zaručujeme, že pokud neopravíte svoje závislosti na co se dodává spolu s .NET Core 1.0, tyto balíčky, budou všechny spolupracovat. Neexistuje žádná taková záruka, pokud používáte balíčky, které nejsou pevné tímto způsobem.

### <a name="scenarios"></a>Scénáře

I když je velký seznam všech balíčků a jejich verze vydané s .NET Core 1.0, nemusí mít si můžete prohlédnout, pokud kód klesne pod určité scénáře.

**Jste si v závislosti na pouze** `NETStandard.Library` **?**

Pokud ano, problém byste měli odstranit vaší `NETStandard.Library` balíček verze `1.6`.  Protože je to kurátorované metapackage, jeho uzavření balíček také vyřešili 1.0.

**Jste si v závislosti na pouze** `Microsoft.NETCore.App` **?**

Pokud ano, problém byste měli odstranit vaší `Microsoft.NETCore.App` balíček verze `1.0.0`.  Protože je to kurátorované metapackage, jeho uzavření balíček také vyřešili 1.0.

**Jste si [oříznutí](../deploying/reducing-dependencies.md) vaše** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metapackage závislosti?**

Pokud ano, měli byste zajistit, že metapackage se vyřešen 1.0.  Jednotlivé balíčky, které závisí na po oříznutí odstraněny také 1.0.

**Jste si v závislosti na balíčky mimo** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metapackages?**

Pokud ano, budete muset vyřešit svoje závislosti do 1.0.  Zjistit verzi správný balíček a sestavte čísla na konci tohoto článku.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Poznámka: na pomocí řetězce splat (\*) při Správa verzí

Přijaly vzor Správa verzí, která používá splat (\*) řetězec takto: `"System.Collections":"4.0.11-*"`.

**Neměli byste**.  Pomocí řetězce splat, může mít za následek obnovují se balíčky z různých sestavení pro některé z nich může být, že se vám dál než .NET Core 1.0.  Výsledkem by mohlo pak některé balíčky se nekompatibilní.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Balíčky a uspořádané podle Metapackage čísla verzí

[Seznam všech balíčků .NET Standard a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Seznam všech balíčků runtime a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Seznam všech balíčků aplikací .NET Core a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
