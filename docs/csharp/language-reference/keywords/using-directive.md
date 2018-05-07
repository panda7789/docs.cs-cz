---
title: using – direktiva (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-directive-c-reference"></a>using – direktiva (Referenční dokumentace jazyka C#)
`using` – Direktiva se třemi způsoby:  
  
-   Chcete-li povolit použití typů v oboru názvů, takže není nutné kvalifikujte použití typu v daném oboru názvů:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Abyste mohli přístup statické členy typu bez nutnosti kvalifikaci přístupu s názvem typu. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Další informace najdete v tématu [pomocí statické direktiva](using-static.md).

-   Chcete-li vytvořit alias oboru názvů, nebo typu. Tento postup se nazývá *pomocí alias – direktiva*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` – Klíčové slovo se také používá k vytvoření *pomocí příkazů*, což pomůže zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písem jsou zpracovány správně. V tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md) Další informace.  
  
## <a name="using-static-type"></a>Pomocí statické typu  
 Statické členy typu se můžete dostat bez nutnosti kvalifikaci přístupu s názvem typu:  
  
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
 Rozsah `using` – direktiva je omezený na soubor, ve kterém se zobrazí.  
  
 Vytvoření `using` alias, aby bylo snazší pro kvalifikaci identifikátor k oboru názvů nebo typu. Na pravé straně pomocí alias direktivy musí být vždy plně kvalifikovaný typ bez ohledu na to, na pomocí direktivy pocházející před ním.  
  
 Vytvoření `using` – direktiva použít typy v oboru názvů bez nutnosti zadávat obor názvů. A `using` – direktiva není poskytnuta přístup na všechny obory názvů, které jsou vnořené v oboru názvů, které zadáte.  
  
 Obory názvů pocházet ve dvou kategoriích: uživatelem definované a definovaná systémem. Uživatelem definované jsou obory názvů definované v kódu. Seznam obory názvů definované v systému, naleznete v části [přehled knihovny tříd rozhraní .NET Framework](../../../standard/class-library-overview.md).  
  
 Příklady na odkazy na metody v ostatních sestavení najdete v tématu [vytvoření a použití sestavení pomocí příkazového řádku](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Příklad 1  
  
 Následující příklad ukazuje, jak definovat a použít `using` alias pro obor názvů:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Using – direktiva alias nemůže mít otevřený obecný typ. na pravé straně. Například nelze vytvořit, pomocí alias seznam\<T >, ale můžete vytvořit seznam\<int >.  
  
## <a name="example-2"></a>Příklad 2  
  
 Následující příklad ukazuje, jak definovat `using` – direktiva a `using` alias pro třídu:  
  
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
