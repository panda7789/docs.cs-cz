---
title: C#Struktura programu – prohlídka C# jazyka
description: Seznamte se se základními stavebními bloky C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5e095e71549ed3eec6c73e6a134fdb5a64fb63c0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884381"
---
# <a name="program-structure"></a>Struktura programu

Klíčovou organizační koncepcí v C# nástroji jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***. C#programy se skládají z jednoho nebo více zdrojových souborů. Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů. Příklady typů jsou třídy a rozhraní. Příklady členů jsou pole, metody, vlastnosti a události. Když C# jsou programy kompilovány, jsou fyzicky zabaleny do sestavení. Sestavení mají obvykle příponu souboru `.exe` nebo `.dll`, v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.

Příklad deklaruje třídu s názvem `Stack` v oboru názvů s názvem `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`. Třída obsahuje několik členů: pole s názvem `top`, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem `Entry`. Třída `Entry` dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor. Za předpokladu, že zdrojový kód příkladu je uložen v souboru `acme.cs`, příkazového řádku

```console
csc /t:library acme.cs
```

zkompiluje příklad jako knihovnu (kód bez `Main` vstupní bod) a vytvoří sestavení s názvem `acme.dll`.

> [!IMPORTANT]
> Výše uvedené příklady používají `csc` jako kompilátor příkazového C# řádku. Tento kompilátor je spustitelný soubor systému Windows. Chcete- C# li používat na jiných platformách, měli byste použít nástroje pro .NET Core. Ekosystém .NET Core používá `dotnet` CLI ke správě sestavení příkazového řádku. To zahrnuje správu závislostí a vyvolávání C# kompilátoru. Úplný popis těchto nástrojů na platformách, které podporuje .NET Core, najdete v [tomto kurzu](../../core/tutorials/cli-create-console-app.md) .

Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat. Před provedením je kód IL v sestavení automaticky převeden na kód specifický pro procesor pomocí kompilátoru JIT (just-in-time) modulu CLR (Common Language Runtime) .NET.

Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktiv a hlavičkových souborů v C#. Veřejné typy a členy, které jsou obsaženy v konkrétním sestavení, jsou v C# programu k dispozici jednoduše odkazem na toto sestavení při kompilování programu. Například tento program používá třídu `Acme.Collections.Stack` ze sestavení `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Pokud je program uložen v souboru `example.cs`, když je `example.cs` kompilováno, může být sestavení Acme. dll odkazováno pomocí možnosti kompilátoru '/r:

```console
csc /r:acme.dll example.cs
```

Tím se vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:

```console
100
10
1
```

C#umožňuje, aby byl zdrojový text programu uložen v několika zdrojových souborech. Když je zkompilován program pro C# více souborů, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat, a to koncepční, protože všechny zdrojové soubory byly před zpracováním sloučeny do jednoho velkého souboru. Dopředné deklarace nejsou nikdy C# potřeba v důsledku nedostatečných výjimek, pořadí deklarací je nedůležité. C#neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](types-and-variables.md)
