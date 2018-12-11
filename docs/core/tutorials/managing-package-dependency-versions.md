---
title: Správa verzí závislosti balíčků pro .NET Core 1.0
description: Další informace o Správa verzí závislosti balíčků pro knihovny .NET Core a aplikace.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168608"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>Správa verzí závislosti balíčků pro .NET Core 1.0

Tento článek popisuje, co potřebujete vědět o verze balíčku pro knihovny .NET Core a aplikace.

## <a name="glossary"></a>Slovníček

**Oprava** – oprava závislostí znamená, že používáte stejné "řady" balíčků vydaných na webu NuGet pro .NET Core 1.0.

**Microsoft.aspnetcore.all** -balíčku A NuGet, který představuje sadu balíčků NuGet.

**Ořezávání** – v rámci balíčky, které nezávisí na odebrání Microsoft.aspnetcore.all.  To je něco, které jsou relevantní pro autory balíčku NuGet.  Zobrazit [omezení závislosti balíčku s project.json](../deploying/reducing-dependencies.md) Další informace. 

## <a name="fix-your-dependencies-to-net-core-10"></a>Oprava závislostí pro .NET Core 1.0

Spolehlivě obnovení balíčků a zápis spolehlivého kódu, je důležité, že oprava závislostí na verze balíčků přesouvání spolu s .NET Core 1.0.  To znamená, že každého balíčku by měl mít jednu verzi se žádné další kvalifikátory.

**Příklady balíčků pevně 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Příklady balíčky, které jsou neopraveno 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Proč to důležité?

Garantujeme, že pokud je oprava závislostí na co se dodává spolu s .NET Core 1.0, tyto balíčky budou všechny spolupracovat. Pokud používáte balíčky, které nejsou pevné tímto způsobem, není zaručeno takové.

### <a name="scenarios"></a>Scénáře

I když existuje velké objemy seznam všechny balíčky a jejich verzí vydané s .NET Core 1.0, pravděpodobně nemáte prohledávat, pokud váš kód v určitých situacích.

**Jste si v závislosti na pouze** `NETStandard.Library` **?**

Pokud ano, by měla vyřešit váš `NETStandard.Library` balíček verze `1.6`.  Protože je to kurátorované Microsoft.aspnetcore.all, jeho uzavření balíčku je také pevně 1.0.

**Jste si v závislosti na pouze** `Microsoft.NETCore.App` **?**

Pokud ano, by měla vyřešit váš `Microsoft.NETCore.App` balíček verze `1.0.0`.  Protože je to kurátorované Microsoft.aspnetcore.all, jeho uzavření balíčku je také pevně 1.0.

**Jste si [oříznutí](../deploying/reducing-dependencies.md) vaše** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **Microsoft.aspnetcore.all závislosti?**

Pokud ano, měli byste zajistit, že je Microsoft.aspnetcore.all, které můžete začít s pevně 1.0.  Jednotlivé balíčky, které závisí na po oříznutí odstraněny také 1.0.

**Jste si v závislosti na balíčky mimo** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metabalíčky?**

Pokud ano, budete muset opravit další závislosti 1.0.  Zobrazit verze správný balíček a sestaví čísel na konci tohoto článku.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Poznámka týkající se použití splat řetězce (\*) při vytváření verzí

Přijali vzor správy verzí, který používá splat (\*) řetězce tímto způsobem: `"System.Collections":"4.0.11-*"`.

**Neměli byste**.  Pomocí řetězce splat by mohlo způsobit obnovují se balíčky z různých sestavení, z nichž některé mohou být dál než .NET Core 1.0.  To může vést některých balíčků není kompatibilních.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Balíčky a čísel verzí uspořádané podle Microsoft.aspnetcore.all

[Seznam všech balíčků pro .NET Standard a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Seznam všech balíčků modulu runtime a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Seznam všech balíčků aplikací .NET Core a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
