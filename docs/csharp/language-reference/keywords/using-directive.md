---
title: Using – direktiva - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 3e8daf24929339e31cda81a726ec11fdcffc687a
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029499"
---
# <a name="using-directive-c-reference"></a>Using – direktiva (C# odkaz)

`using` – Direktiva má tři používá:

- Chcete-li povolit použití typů v oboru názvů, takže není potřeba kvalifikovat použití typu v tomto oboru názvů:

    ```csharp
    using System.Text;
    ```

- Aby bylo možné přistupovat ke statické členy a vnořené typy typu bez nutnosti kvalifikovat přístup k s názvem typu.

    ```csharp
    using static System.Math;
    ```

    Další informace najdete v tématu [using static – direktiva](using-static.md).

- Chcete-li vytvořit alias pro obor názvů nebo typu. Tento postup se nazývá *alias direktiva using*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

`using` – Klíčové slovo se také používá k vytvoření *příkazy using*, které pomáhají zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písma jsou správně zpracovány. Zobrazit [příkaz using](using-statement.md) Další informace.

## <a name="using-static-type"></a>Pomocí statického typu

Statické členy typu přístupné bez nutnosti kvalifikovat přístup k s názvem typu:

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

Rozsah `using` – direktiva je omezená na soubor, ve kterém se zobrazí.

`using` – Direktiva se může objevit:

- Na začátku souboru zdrojového kódu, než všechny obor názvů nebo typ definice.
- V jakékoli obor názvů, ale před jakoukoli oboru názvů nebo typy deklarované v tomto oboru názvů.

Jinak Chyba kompilátoru [CS1529](../../misc/cs1529.md) je generován.

Vytvoření `using` alias – direktiva zjednodušit zařadit do oboru názvů nebo typ identifikátoru. V žádném `using` direktiv, plně kvalifikovaný obor názvů nebo typ musí být použita bez ohledu na to `using` direktivy, které jej předcházejí. Ne `using` alias lze použít v deklaraci `using` směrnice. Následující příklad vygeneruje chybu kompilátoru:

```csharp
using s = System.Text;
using s.RegularExpressions;
```

Vytvoření `using` směrnice použít typy v oboru názvů, aniž byste museli zadat obor názvů. A `using` – direktiva není poskytují přístup k žádné obory názvů, které jsou vnořené v oboru názvů, které zadáte.

Obory názvů se dělí na dvou kategorií: uživatelem definované a definovaná systémem. Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam oborů názvů definovaných systémem najdete v tématu [.NET API Browseru](../../../../api/index.md).

Odkazující metody v jiných sestaveních příklady najdete v tématu [vytvoření a použití sestavení pomocí příkazového řádku](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak definovat a používat `using` alias pro obor názvů:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Using – direktiva alias nemůže mít otevřený obecný typ. na pravé straně. Například nemůžete vytvořit alias using pro `List<T>`, ale můžete ho vytvořit `List<int>`.

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje, jak definovat `using` směrnice a `using` alias pro třídu:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [direktiv Using](~/_csharplang/spec/namespaces.md#using-directives) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Použití oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova oboru názvů](namespace-keywords.md)
- [Obory názvů](../../programming-guide/namespaces/index.md)
- [using – příkaz](using-statement.md)
