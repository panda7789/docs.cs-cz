---
title: použití direktivy – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093146"
---
# <a name="using-directive-c-reference"></a>pomocí směrnice (C# Reference)

Směrnice `using` má tři použití:

- Chcete-li povolit použití typů v oboru názvů, abyste nemuseli kvalifikovat použití typu v tomto oboru názvů:

    ```csharp
    using System.Text;
    ```

- Chcete-li povolit přístup ke statickým členům a vnořeným typům, aniž byste museli kvalifikovat přístup s názvem typu.

    ```csharp
    using static System.Math;
    ```

    Další informace naleznete v [tématu using static directive](using-static.md).

- Vytvoření aliasu pro obor názvů nebo typ. To se nazývá *using alias směrnice*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Klíčové `using` slovo se také používá k vytvoření <xref:System.IDisposable> pomocí *příkazů*, které pomáhají zajistit, že objekty, jako jsou soubory a písma jsou zpracovány správně. Další informace najdete [v tématu použití příkazu.](using-statement.md)

## <a name="using-static-type"></a>Použití statického typu

Můžete přistupovat ke statickým členům typu, aniž byste museli kvalifikovat přístup s názvem typu:

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a>Poznámky

Oblast působnosti `using` směrnice je omezena na soubor, ve kterém se objevuje.

Směrnice `using` se může objevit:

- Na začátku souboru zdrojového kódu před všemi definicemi oboru názvů nebo typu.
- V libovolném oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.

V opačném případě je generována chyba kompilátoru [CS1529.](../../misc/cs1529.md)

Vytvořte `using` direktivu aliasu, která usnadní kvalifikaci identifikátoru do oboru názvů nebo typu. V `using` každé direktivě musí být použit plně kvalifikovaný `using` obor názvů nebo typ bez ohledu na direktivy, které jsou před ním. V `using` deklaraci `using` směrnice nelze použít žádný alias. Například následující generuje chybu kompilátoru:

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

Vytvořte `using` direktivu pro použití typů v oboru názvů bez nutnosti zadávat obor názvů. Direktiva `using` neposkytuje přístup k žádným oborům názvů, které jsou vnořeny do zadaného oboru názvů.

Obory názvů jsou dodávány ve dvou kategoriích: uživatelem definované a definované systémem. Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam systémově definovaných oborů názvů naleznete v [tématu .NET API Browser](../../../../api/index.md).

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak definovat `using` a používat alias pro obor názvů:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Direktiva using alias nemůže mít otevřený obecný typ na pravé straně. Nemůžete například vytvořit using alias `List<T>`pro , ale můžete `List<int>`jej vytvořit pro .

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje, jak `using` definovat `using` direktivu a alias pro třídu:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v [tématu Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Použití oborů názvů](../../programming-guide/namespaces/using-namespaces.md)
- [C# Klíčová slova](index.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
- [using – příkaz](using-statement.md)
