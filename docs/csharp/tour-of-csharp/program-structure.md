---
title: C# Struktura programu - Prohlídka jazyka C#
description: Naučte se základní stavební kameny programu C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156828"
---
# <a name="program-structure"></a>Struktura programu

Klíčovými organizačními koncepty v c# jsou ***programy***, ***obory názvů***, ***typy***, ***členové***a ***sestavení***. Programy jazyka C# se skládají z jednoho nebo více zdrojových souborů. Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů. Třídy a rozhraní jsou příklady typů. Pole, metody, vlastnosti a události jsou příklady členů. Při kompilaci c# programy jsou fyzicky zabaleny do sestavení. Sestavení mají obvykle `.exe` příponu `.dll`souboru nebo v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***.

Pomocí příkazu můžete vytvořit projekt knihovny `dotnet new` s názvem *acme:*

```console
dotnet new classlib -o acme
```

V tomto projektu deklarujte třídu pojmenovanou `Stack` v oboru názvů s názvem `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Plně kvalifikovaný název této `Acme.Collections.Stack`třídy je . Třída obsahuje několik členů: `top`pole s `Push` názvem `Pop`, dvě metody `Entry`s názvem a , a vnořenou třídu s názvem . Třída `Entry` dále obsahuje tři členy: `next`pole s `data`názvem , pole s názvem a konstruktor. Příkaz:

```console
dotnet build
```

zkompiluje příklad jako knihovnu (kód bez `Main` vstupního `acme.dll`bodu) a vytvoří sestavení s názvem .

Sestavení obsahují spustitelný kód ve formě pokynů zprostředkujícího jazyka (IL) a symbolické informace ve formě metadat. Před jeho spuštěním převede kompilátor Just-In-Time (JIT) rozhraní .NET Common Language Runtime kód IL v sestavení na kód specifický pro procesor.

Vzhledem k tomu, že sestavení je vlastní popisující jednotka funkcí obsahující kód i `#include` metadata, není potřeba direktiv y a souborů hlaviček v systému C#. Veřejné typy a členy obsažené v určitém sestavení jsou k dispozici v programu Jazyka C# jednoduše odkazováním na toto sestavení při kompilaci programu. Tento program například `Acme.Collections.Stack` používá třídu ze `acme.dll` sestavení:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Soubor *csproj* pro předchozí program projektu musí obsahovat referenční uzel pro kompilátor Jazyka C#, `acme.dll` aby bylo možné vyřešit odkazy na třídy v sestavení:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Po tomto `dotnet build` přidání vytvoří spustitelný `example.exe`sestavení s názvem , který při spuštění vytvoří výstup:

```console
100
10
1
```

C# umožňuje zdrojový text programu, které mají být uloženy v několika zdrojových souborů. Při kompilaci vícesouborového programu Jazyka C# jsou všechny zdrojové soubory zpracovány společně a zdrojové soubory mohou volně odkazovat na sebe – koncepčně, je to, jako by všechny zdrojové soubory byly před zpracováním zřetězeny do jednoho velkého souboru. Forward deklarace jsou nikdy potřeba v C# protože s několika výjimkami pořadí deklarace je nevýznamné. C# neomezuje zdrojový soubor na deklarování pouze jednoho veřejného typu ani nevyžaduje název zdrojového souboru tak, aby odpovídal typu deklarovanému ve zdrojovém souboru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](types-and-variables.md)
