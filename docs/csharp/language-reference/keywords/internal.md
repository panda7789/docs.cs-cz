---
title: internal (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523358"
---
# <a name="internal-c-reference"></a><span data-ttu-id="9657a-102">internal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9657a-102">internal (C# Reference)</span></span>
<span data-ttu-id="9657a-103">`internal` – Klíčové slovo je [modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="9657a-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="9657a-104">Tato stránka popisuje `internal` přístup.</span><span class="sxs-lookup"><span data-stu-id="9657a-104">This page covers `internal` access.</span></span> <span data-ttu-id="9657a-105">`internal` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="9657a-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="9657a-106">Vnitřní typy nebo členy jsou přístupné jenom v souborech ve stejném sestavení, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9657a-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="9657a-107">Porovnání `internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9657a-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9657a-108">Další informace o sestavení, naleznete v tématu [sestavení a globální mezipaměť sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="9657a-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="9657a-109">Běžné použití interního přístupu je ve vývoji založených na komponentách, protože umožňuje skupina součástí privátní způsobem spolupracovat bez zasahování přímo do zbytku kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9657a-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="9657a-110">Například může poskytovat architekturu pro tvorbu grafické uživatelské rozhraní `Control` a `Form` třídy, které spolupracují s použitím členy mají interní přístup.</span><span class="sxs-lookup"><span data-stu-id="9657a-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="9657a-111">Vzhledem k tomu, že tyto členy jsou interní, že nejsou zveřejněné kód, který používá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9657a-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="9657a-112">Jedná se o chybu, chcete-li odkazovat typ nebo člen interní přístup mimo sestavení, ve kterém byl definován.</span><span class="sxs-lookup"><span data-stu-id="9657a-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9657a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9657a-113">Example</span></span>  
 <span data-ttu-id="9657a-114">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="9657a-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="9657a-115">První soubor obsahuje interní základní třída, `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="9657a-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="9657a-116">V souboru druhý pokus o vytvoření instance `BaseClass` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="9657a-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9657a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="9657a-117">Example</span></span>  
 <span data-ttu-id="9657a-118">V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1 a změňte úroveň usnadnění `BaseClass` k `public`.</span><span class="sxs-lookup"><span data-stu-id="9657a-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="9657a-119">Také změnit úroveň přístupnost člena `IntM` k `internal`.</span><span class="sxs-lookup"><span data-stu-id="9657a-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="9657a-120">V takovém případě můžete vytvořit instanci třídy, ale k interní členu nelze přistupovat.</span><span class="sxs-lookup"><span data-stu-id="9657a-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="9657a-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9657a-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9657a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9657a-122">See Also</span></span>

- [<span data-ttu-id="9657a-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9657a-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9657a-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9657a-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9657a-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9657a-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9657a-126">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9657a-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="9657a-127">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="9657a-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="9657a-128">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="9657a-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="9657a-129">public</span><span class="sxs-lookup"><span data-stu-id="9657a-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="9657a-130">private</span><span class="sxs-lookup"><span data-stu-id="9657a-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="9657a-131">protected</span><span class="sxs-lookup"><span data-stu-id="9657a-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
