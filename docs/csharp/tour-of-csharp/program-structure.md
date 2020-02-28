---
title: C#Struktura programu – prohlídka C# jazyka
description: Seznamte se se základními stavebními bloky C# programu
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159114"
---
# <a name="program-structure"></a>Struktura programu

Klíčovou organizační koncepcí v C# nástroji jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***. C#programy se skládají z jednoho nebo více zdrojových souborů. Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů. Příklady typů jsou třídy a rozhraní. Příklady členů jsou pole, metody, vlastnosti a události. Když C# jsou programy kompilovány, jsou fyzicky zabaleny do sestavení. Sestavení mají obvykle příponu souboru `.exe` nebo `.dll`, v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.

Projekt knihovny s názvem *ACME* můžete vytvořit pomocí příkazu `dotnet new`:

```console
dotnet new classlib -o acme
```

V tomto projektu Deklarujte třídu s názvem `Stack` v oboru názvů s názvem `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`. Třída obsahuje několik členů: pole s názvem `top`, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem `Entry`. Třída `Entry` dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor. Příkaz:

```console
dotnet build 
```

zkompiluje příklad jako knihovnu (kód bez `Main` vstupní bod) a vytvoří sestavení s názvem `acme.dll`.

Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat. Předtím, než se spustí, kompilátor JIT (just-in-time) prostředí .NET Common Language Runtime převede kód IL v sestavení na kód specifický pro procesor.

Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktiv a hlavičkových souborů v C#. Veřejné typy a členy, které jsou obsaženy v konkrétním sestavení, jsou v C# programu k dispozici jednoduše odkazem na toto sestavení při kompilování programu. Například tento program používá třídu `Acme.Collections.Stack` ze sestavení `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Soubor *csproj* pro projekt předchozí aplikace musí zahrnovat uzel odkazu pro C# kompilátor, aby vyřešil odkazy na třídy v sestavení `acme.dll`:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po přidání `dotnet build` vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:

```console
100
10
1
```

C#umožňuje, aby byl zdrojový text programu uložen v několika zdrojových souborech. Když je zkompilován program pro C# více souborů, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat, a to koncepční, protože všechny zdrojové soubory byly před zpracováním sloučeny do jednoho velkého souboru. Předávací deklarace nejsou nikdy potřeba v C# rámci, protože s malým počtem výjimek je pořadí deklarací nedůležité. C#neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](types-and-variables.md)
