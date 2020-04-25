---
title: Struktura programu v jazyce c# – prohlídka jazyka C#
description: Seznamte se se základními stavebními bloky programu v jazyce C#.
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141016"
---
# <a name="program-structure"></a>Struktura programu

Klíčovou organizační koncepcí v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***. Programy v jazyce C# se skládají z jednoho nebo více zdrojových souborů. Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů. Příklady typů jsou třídy a rozhraní. Příklady členů jsou pole, metody, vlastnosti a události. Když jsou programy C# kompilovány, jsou fyzicky zabaleny do sestavení. Sestavení mají `.exe` obvykle příponu souboru nebo `.dll`v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.

Projekt knihovny s názvem *ACME* můžete vytvořit pomocí `dotnet new` příkazu:

```dotnetcli
dotnet new classlib -o acme
```

V tomto projektu Deklarujte třídu s názvem `Stack` v oboru názvů s `Acme.Collections`názvem:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`. Třída obsahuje několik členů: pole s `top`názvem, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem. `Entry` `Entry` Třída dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor. Příkaz:

```dotnetcli
dotnet build
```

zkompiluje příklad jako knihovnu (kód bez `Main` vstupního bodu) a vytvoří sestavení s názvem. `acme.dll`

Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat. Předtím, než se spustí, kompilátor JIT (just-in-time) prostředí .NET Common Language Runtime převede kód IL v sestavení na kód specifický pro procesor.

Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktivy a hlavičkové soubory v jazyce C#. Veřejné typy a členy obsažené v konkrétním sestavení jsou zpřístupněny v programu v jazyce C# pouhým odkazováním na toto sestavení při kompilování programu. Například tento program používá `Acme.Collections.Stack` třídu ze `acme.dll` sestavení:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Soubor *csproj* pro projekt předchozí aplikace musí obsahovat referenční uzel pro kompilátor jazyka C#, který bude překládat odkazy na třídy v `acme.dll` sestavení:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po tomto přidání `dotnet build` vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:

```dotnetcli
100
10
1
```

Jazyk C# umožňuje uložit zdrojový text programu do několika zdrojových souborů. Když je zkompilován program pro více souborů C#, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat – koncepčně, je to tak, aby byly všechny zdrojové soubory zřetězeny do jednoho velkého souboru před zpracováním. Předávací deklarace nejsou v jazyce C# nikdy potřeba, protože s malým počtem výjimek je pořadí deklarací nedůležité. Jazyk C# neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](types-and-variables.md)
