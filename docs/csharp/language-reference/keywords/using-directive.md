---
title: Direktiva using C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970047"
---
# <a name="using-directive-c-reference"></a>using – direktiva (C# Referenční dokumentace)

`using` Direktiva má tři použití:

- Aby bylo možné povolit použití typů v oboru názvů, takže nemusíte kvalifikovat použití typu v tomto oboru názvů:

    ```csharp
    using System.Text;
    ```

- Aby bylo možné přistupovat ke statickým členům a vnořeným typům typu bez nutnosti kvalifikovat přístup s názvem typu.

    ```csharp
    using static System.Math;
    ```

    Další informace naleznete v [direktivě using static](using-static.md).

- Pro vytvoření aliasu pro obor názvů nebo typ. Tato *direktiva se nazývá using alias*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Klíčové slovo slouží také k vytváření *příkazů using*, které vám pomůžou zajistit <xref:System.IDisposable> , aby objekty, jako jsou soubory a písma, byly zpracovávány správně. `using` Další informace najdete v tématu [použití příkazu Using](using-statement.md) .

## <a name="using-static-type"></a>Použití statického typu

Můžete přistupovat ke statickým členům typu bez nutnosti kvalifikovat přístup s názvem typu:

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

Rozsah `using` direktivy je omezen na soubor, ve kterém se zobrazí.

Tato `using` direktiva se může zobrazit:

- Na začátku souboru zdrojového kódu před libovolným oborem názvů nebo definicí typu.
- V jakémkoli oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.

V opačném případě se generuje chyba kompilátoru [CS1529](../../misc/cs1529.md) .

Vytvořte direktivu `using` alias pro snadnější zařazení identifikátoru do oboru názvů nebo typu. V jakékoli `using` direktivě musí být plně kvalifikovaný obor názvů nebo typ použit bez ohledu na `using` direktivy, které jsou před ním. V `using` deklaraci `using` direktivy nelze použít žádný alias. Například následující příkaz vygeneruje chybu kompilátoru:

```csharp
using s = System.Text;
using s.RegularExpressions;
```

`using` Vytvořte direktivu pro použití typů v oboru názvů bez nutnosti zadat obor názvů. `using` Direktiva neposkytuje přístup k žádným oborům názvů, které jsou vnořené v oboru názvů, který zadáte.

Obory názvů přicházejí ve dvou kategoriích: definované uživatelem a systémem. Uživatelsky definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam oborů názvů definovaných systémem naleznete v tématu [.NET API Browser](../../../../api/index.md).

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak definovat a použít `using` alias pro obor názvů:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Direktiva using alias nemůže mít otevřený obecný typ na pravé straně. Například nemůžete vytvořit alias s aliasem pro `List<T>`, ale můžete ho vytvořit `List<int>`pro.

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje, jak definovat `using` direktivu `using` a alias pro třídu:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [direktivy using](~/_csharplang/spec/namespaces.md#using-directives) ve [ C# specifikaci jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Klíčová slova jazyka C#](index.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
- [using – příkaz](using-statement.md)
