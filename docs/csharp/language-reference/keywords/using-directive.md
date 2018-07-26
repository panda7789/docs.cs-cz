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
# <a name="using-directive-c-reference"></a><span data-ttu-id="d2b67-102">using – direktiva (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d2b67-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="d2b67-103">`using` – Direktiva má tři používá:</span><span class="sxs-lookup"><span data-stu-id="d2b67-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="d2b67-104">Chcete-li povolit použití typů v oboru názvů, takže není potřeba kvalifikovat použití typu v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="d2b67-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="d2b67-105">Aby bylo možné přistupovat ke statické členy typu bez nutnosti kvalifikovat přístup k s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="d2b67-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="d2b67-106">Další informace najdete v tématu [using static – direktiva](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="d2b67-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="d2b67-107">Chcete-li vytvořit alias pro obor názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="d2b67-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="d2b67-108">Tento postup se nazývá *alias direktiva using*.</span><span class="sxs-lookup"><span data-stu-id="d2b67-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="d2b67-109">`using` – Klíčové slovo se také používá k vytvoření *příkazy using*, které pomáhají zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písma jsou správně zpracovány.</span><span class="sxs-lookup"><span data-stu-id="d2b67-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="d2b67-110">Zobrazit [příkaz using](../../../csharp/language-reference/keywords/using-statement.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="d2b67-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="d2b67-111">Pomocí statického typu</span><span class="sxs-lookup"><span data-stu-id="d2b67-111">Using Static Type</span></span>  
 <span data-ttu-id="d2b67-112">Statické členy typu přístupné bez nutnosti kvalifikovat přístup k s názvem typu:</span><span class="sxs-lookup"><span data-stu-id="d2b67-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="d2b67-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2b67-113">Remarks</span></span>  
 <span data-ttu-id="d2b67-114">Rozsah `using` – direktiva je omezená na soubor, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d2b67-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="d2b67-115">Vytvoření `using` aliasu, aby bylo snazší zařadit do oboru názvů nebo typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d2b67-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="d2b67-116">Na pravé straně pomocí alias direktiv musí být vždy plně kvalifikovaný typ bez ohledu na to, pomocí direktivy, které jej předcházejí.</span><span class="sxs-lookup"><span data-stu-id="d2b67-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="d2b67-117">Vytvoření `using` směrnice použít typy v oboru názvů, aniž byste museli zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d2b67-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="d2b67-118">A `using` – direktiva není poskytují přístup k žádné obory názvů, které jsou vnořené v oboru názvů, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="d2b67-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="d2b67-119">Obory názvů se dělí na dvou kategorií: uživatelem definované a definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="d2b67-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="d2b67-120">Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="d2b67-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="d2b67-121">Seznam oborů názvů definovaných systémem najdete v tématu [přehled knihovny tříd rozhraní .NET Framework](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2b67-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="d2b67-122">Odkazující metody v jiných sestaveních příklady najdete v tématu [vytvoření a použití sestavení pomocí příkazového řádku](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="d2b67-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="d2b67-123">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="d2b67-123">Example 1</span></span>  
  
 <span data-ttu-id="d2b67-124">Následující příklad ukazuje, jak definovat a používat `using` alias pro obor názvů:</span><span class="sxs-lookup"><span data-stu-id="d2b67-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="d2b67-125">Using – direktiva alias nemůže mít otevřený obecný typ. na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="d2b67-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="d2b67-126">Například nelze vytvořit alias using seznam\<T >, ale můžete vytvořit jeden seznam\<int >.</span><span class="sxs-lookup"><span data-stu-id="d2b67-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="d2b67-127">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="d2b67-127">Example 2</span></span>  
  
 <span data-ttu-id="d2b67-128">Následující příklad ukazuje, jak definovat `using` směrnice a `using` alias pro třídu:</span><span class="sxs-lookup"><span data-stu-id="d2b67-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2b67-129">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b67-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2b67-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2b67-130">See Also</span></span>  
 [<span data-ttu-id="d2b67-131">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b67-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d2b67-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d2b67-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d2b67-133">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="d2b67-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="d2b67-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b67-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d2b67-135">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="d2b67-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="d2b67-136">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="d2b67-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="d2b67-137">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="d2b67-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
