---
title: using – direktiva (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 1ed7ac49cde6792cddff898e8b9930a83598e02c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514544"
---
# <a name="using-directive-c-reference"></a>using – direktiva (Referenční dokumentace jazyka C#)
`using` – Direktiva má tři používá:  
  
-   Chcete-li povolit použití typů v oboru názvů, takže není potřeba kvalifikovat použití typu v tomto oboru názvů:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Aby bylo možné přistupovat ke statické členy a vnořené typy typu bez nutnosti kvalifikovat přístup k s názvem typu. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Další informace najdete v tématu [using static – direktiva](using-static.md).

-   Chcete-li vytvořit alias pro obor názvů nebo typu. Tento postup se nazývá *alias direktiva using*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` – Klíčové slovo se také používá k vytvoření *příkazy using*, které pomáhají zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písma jsou správně zpracovány. Zobrazit [příkaz using](../../../csharp/language-reference/keywords/using-statement.md) Další informace.  
  
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
  
 Obory názvů se dělí na dvou kategorií: uživatelem definované a definovaná systémem. Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam oborů názvů definovaných systémem najdete v tématu [.NET API Browseru](https://docs.microsoft.com/en-us/dotnet/api/).  
  
 Odkazující metody v jiných sestaveních příklady najdete v tématu [vytvoření a použití sestavení pomocí příkazového řádku](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Příklad 1  
  
 Následující příklad ukazuje, jak definovat a používat `using` alias pro obor názvů:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Using – direktiva alias nemůže mít otevřený obecný typ. na pravé straně. Například nelze vytvořit alias using seznam\<T >, ale můžete vytvořit jeden seznam\<int >.  
  
## <a name="example-2"></a>Příklad 2  
  
 Následující příklad ukazuje, jak definovat `using` směrnice a `using` alias pro třídu:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
- [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)
