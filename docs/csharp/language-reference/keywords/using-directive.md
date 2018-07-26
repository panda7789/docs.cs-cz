---
title: using – direktiva (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960037"
---
# <a name="using-directive-c-reference"></a>using – direktiva (Referenční dokumentace jazyka C#)
`using` – Direktiva má tři používá:  
  
-   Chcete-li povolit použití typů v oboru názvů, takže není potřeba kvalifikovat použití typu v tomto oboru názvů:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Aby bylo možné přistupovat ke statické členy typu bez nutnosti kvalifikovat přístup k s názvem typu. 
  
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
  
 Vytvoření `using` aliasu, aby bylo snazší zařadit do oboru názvů nebo typ identifikátoru. Na pravé straně pomocí alias direktiv musí být vždy plně kvalifikovaný typ bez ohledu na to, pomocí direktivy, které jej předcházejí.  
  
 Vytvoření `using` směrnice použít typy v oboru názvů, aniž byste museli zadat obor názvů. A `using` – direktiva není poskytují přístup k žádné obory názvů, které jsou vnořené v oboru názvů, které zadáte.  
  
 Obory názvů se dělí na dvou kategorií: uživatelem definované a definovaná systémem. Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu. Seznam oborů názvů definovaných systémem najdete v tématu [přehled knihovny tříd rozhraní .NET Framework](../../../standard/class-library-overview.md).  
  
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
 [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)
