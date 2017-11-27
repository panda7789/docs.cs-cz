---
title: "C# Program strukturu – přehled používání jazyka C#"
description: "Další základní stavební bloky programu v C#"
keywords: "Rozhraní .NET .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a>Struktura programu

Klíčové koncepty organizace v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***, a ***sestavení***. Programy C# obsahovat jeden nebo více zdrojových souborů. Programy deklarovat typy, které obsahují členy a mohou být uspořádány do oborů názvů. Třídy a rozhraní jsou příklady typů. Pole, metody, vlastnosti a události jsou příklady členů. Když jsou kompilované programy C#, jsou fyzicky zabalené do sestavení. Sestavení obvykle mají příponu souboru `.exe` nebo `.dll`, v závislosti na tom, jestli implementace ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.

V příkladu deklaruje třídy s názvem `Stack` v oboru názvů názvem `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`. Třída obsahuje několik členů: pole s názvem `top`, dvě metody s názvem `Push` a `Pop`a vnořené třídy s názvem `Entry`. `Entry` Další třída obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor. Za předpokladu, že zdrojový kód v příkladu je uložené v souboru `acme.cs`, příkazového řádku

```
csc /t:library acme.cs
```

zkompiluje v příkladu jako knihovny (code bez `Main` vstupního bodu) a vytvoří sestavení s názvem `acme.dll`.

> [!IMPORTANT]
> Příklady výše použití `csc` jako kompilátoru příkazového řádku jazyka C#. Tato kompilátoru je spustitelný soubor windows. Pokud chcete používat C# na jiných platformách, by měl pomocí nástrojů pro .NET Core. Používá ekosystému .NET Core `dotnet` rozhraní příkazového řádku pro správu sestavení příkazového řádku. To zahrnuje správu závislosti a volání do kompilátoru jazyka C#. V tématu [v tomto kurzu](../../core/tutorials/using-with-xplat-cli.md) úplný popis těchto nástrojů na platformách podporovaných aplikací .NET Core.

Sestavení obsahovat spustitelného kódu ve formě pokyny Intermediate Language (IL) a symbolické informace ve formě metadat. Před provedením, kód IL v sestavení automaticky převeden na specifické pro procesor kód kompilátorem JIT (JIT) Common Language Runtime rozhraní .NET.

Protože sestavení je popisující samy sebe jednotka funkce obsahující kód a metadata, není nutné pro `#include` direktivy a hlavičkových souborů v jazyce C#. Veřejné typy a členy obsažené v určitém sestavení jsou k dispozici v programu v C# jednoduše tak, že odkazování na sestavení při kompilaci programu. Například používá tento program `Acme.Collections.Stack` třídy z `acme.dll` sestavení:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Pokud je program uložen v souboru `example.cs`, když `example.cs` je kompilovat, sestavení acme.dll můžete odkazovat pomocí /r – možnost kompilátoru:

```
csc /r:acme.dll example.cs
```

Tím se vytvoří spustitelný soubor sestavení s názvem `example.exe`, které, když se spustí, vytvoří výstup:

```
100
10
1
```

C# umožňuje zdrojový text programu, který má být uložen v několika zdrojové soubory. Při kompilaci více soubory programu v C#, všechny zdrojové soubory jsou zpracovávány společně, a zdrojové soubory můžete volně odkazovat navzájem – koncepčně, je jako kdyby byly všechny zdrojové soubory zřetězen do jednoho velkého souboru před zpracováním. Předat dál deklarace jsou nikdy potřeba v jazyce C#, protože s počtu výjimek je zanedbatelný deklarace pořadí. C# neomezuje zdrojového souboru do deklarace pouze jeden typ veřejné ani nevyžaduje název zdrojového souboru tak, aby odpovídaly typu deklarovaného v souboru zdroje.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](types-and-variables.md)
