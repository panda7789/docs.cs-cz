---
title: C#Program strukturu – připravuje C# jazyka
description: Přečtěte si základní stavební bloky C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: e6b3e0d3b91d3dee8cbc8ac530323e23e0ce8b2a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634564"
---
# <a name="program-structure"></a>Struktura programu

Klíčové koncepty organizace v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***, a ***sestavení***. Programy jazyka C# se skládají z jednoho nebo více zdrojových souborů. Programy deklarovat typy, které obsahují členy a mohou být uspořádány do oborů názvů. Třídy a rozhraní jsou příklady typů. Pole, metody, vlastnosti a události jsou příklady členů. Když jsou kompilovány programy jazyka C#, jsou fyzicky zabaleny do sestavení. Sestavení obvykle mít příponu souboru `.exe` nebo `.dll`, v závislosti na tom, jestli je implementovat ***aplikací*** nebo ***knihovny***v uvedeném pořadí.

Příklad deklaruje třídu s názvem `Stack` v obor názvů s názvem `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`. Třída obsahuje několik členů: pole s názvem `top`, dvě metody s názvem `Push` a `Pop`a vnořené třídy s názvem `Entry`. `Entry` Další třídy obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor. Za předpokladu, že zdrojový kód v příkladu je uložen v souboru `acme.cs`, příkazového řádku

```
csc /t:library acme.cs
```

zkompiluje v příkladu jako knihovna (bez kódu `Main` vstupního bodu) a vytváří sestavení s názvem `acme.dll`.

> [!IMPORTANT]
> Příklady nad použití `csc` jako příkazového řádku C# kompilátoru. Tento kompilátor je spustitelný soubor Windows. Chcete-li použít C# na jiných platformách, by měly použít nástroje pro .NET Core. Používá ekosystému .NET Core `dotnet` CLI ke správě sestavení příkazového řádku. To zahrnuje správu závislostí a vyvolání C# kompilátoru. Zobrazit [v tomto kurzu](../../core/tutorials/using-with-xplat-cli.md) úplný popis těchto nástrojů na platformách podporovaných aplikací .NET Core.

Sestavení obsahují spustitelného kódu v podobě pokynů Intermediate Language (IL) a symbolické informace ve formě metadat. Předtím, než se spustí, kód IL v sestavení automaticky převést do kódu specifického pro procesor kompilátorem za běhu (JIT) modulu .NET Common Language Runtime.

Protože sestavení je jednotka funkce obsahující kód a metadata popisující samy sebe, není nutné pro `#include` direktivy a soubory hlaviček v jazyce C#. Veřejné typy a členy, které jsou obsažené v konkrétní sestavení jsou k dispozici v programu v jazyce C# jednoduše tak, že odkazující na toto sestavení při kompilaci programu. Například používá tento program `Acme.Collections.Stack` třídy z `acme.dll` sestavení:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Pokud program je uložený v souboru `example.cs`, když `example.cs` je zkompilován, acme.dll sestavení lze odkazovat pomocí /r – možnost kompilátoru:

```
csc /r:acme.dll example.cs
```

Tím se vytvoří sestavení spustitelného souboru s názvem `example.exe`, který při spuštění vytvoří výstup:

```
100
10
1
```

C# umožňuje text zdrojového programu, který bude uložen do několika zdrojových souborů. Když je zkompilován více soubory programu v C#, jsou společně zpracovány všechny zdrojové soubory a zdrojové soubory můžete odkazovat na volně mezi sebou, koncepčně, je, jako kdyby byly všechny zdrojové soubory zřetězeny do jednoho velkého souboru před zpracováním. Dopředné deklarace jsou potřeba nikdy v jazyce C#, protože s několika málo výjimkami je deklarace pořadí je neplatné. C# neomezuje zdrojový soubor k deklarování pouze jeden veřejný typ taky je potřeba, aby název zdrojového souboru tak, aby odpovídaly typu deklarovaného ve zdrojovém souboru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](types-and-variables.md)
