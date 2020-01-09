---
title: Direktiva using C# – referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: a2028ccce47de54b59323194a0ffab3a643d878c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712972"
---
# <a name="using-directive-c-reference"></a>using – direktiva (C# Referenční dokumentace)

Direktiva `using` má tři použití:

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

Klíčové slovo `using` slouží také k vytváření *příkazů using*, které umožňují zajistit správné zpracování objektů <xref:System.IDisposable>, jako jsou soubory a písma. Další informace najdete v tématu [použití příkazu Using](using-statement.md) .

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

Rozsah direktivy `using` je omezený na soubor, ve kterém se zobrazí.

Může se zobrazit direktiva `using`:

- Na začátku souboru zdrojového kódu před libovolným oborem názvů nebo definicí typu.
- V jakémkoli oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.

V opačném případě se generuje chyba kompilátoru [CS1529](../../misc/cs1529.md) .

Vytvořte direktivu `using` alias, aby bylo snazší kvalifikovat identifikátor oboru názvů nebo typu. V jakékoli `using` direktivě musí být plně kvalifikovaný obor názvů nebo typ použit bez ohledu na direktivy `using`, které jsou před ním. V deklaraci direktivy `using` nelze použít žádný alias `using`. Například následující příkaz vygeneruje chybu kompilátoru:

```csharp
using s = System.Text;
using s.RegularExpressions;
```

Vytvořte direktivu `using` pro použití typů v oboru názvů bez nutnosti zadat obor názvů. Direktiva `using` neposkytuje přístup k žádným oborům názvů, které jsou vnořené v oboru názvů, který zadáte.

Obory názvů přicházejí ve dvou kategoriích: definované uživatelem a systémem. Uživatelsky definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam oborů názvů definovaných systémem naleznete v tématu [.NET API Browser](../../../../api/index.md).

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak definovat a použít alias `using` pro obor názvů:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Direktiva using alias nemůže mít otevřený obecný typ na pravé straně. Například nemůžete vytvořit alias alias pro `List<T>`, ale můžete ho vytvořit pro `List<int>`.

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje, jak definovat direktivu `using` a alias `using` pro třídu:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [direktivy using](~/_csharplang/spec/namespaces.md#using-directives) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Klíčová slova jazyka C#](index.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
- [using – příkaz](using-statement.md)
