---
description: Reference interního jazyka C#
title: Reference interního jazyka C#
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 14722d66a65eb5f96118acf017dc877e657b2dd9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134572"
---
# <a name="internal-c-reference"></a><span data-ttu-id="88f69-103">internal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88f69-103">internal (C# Reference)</span></span>
<span data-ttu-id="88f69-104">`internal`Klíčové slovo je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typů.</span><span class="sxs-lookup"><span data-stu-id="88f69-104">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="88f69-105">Tato stránka se zabývá `internal` přístupem.</span><span class="sxs-lookup"><span data-stu-id="88f69-105">This page covers `internal` access.</span></span> <span data-ttu-id="88f69-106">`internal`Klíčové slovo je také součástí [`protected internal`](./protected-internal.md) modifikátoru přístupu.</span><span class="sxs-lookup"><span data-stu-id="88f69-106">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="88f69-107">Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="88f69-107">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="88f69-108">Porovnání `internal` s dalšími modifikátory přístupu najdete v tématu [úrovně přístupnosti](./accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="88f69-108">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="88f69-109">Další informace o sestaveních naleznete [v tématu sestavení v rozhraní .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="88f69-109">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="88f69-110">Běžné použití interního přístupu je v rámci vývoje založeného na komponentách, protože umožňuje skupině komponent, aby spolupracovaly soukromě, aniž by bylo zveřejněno pro zbytek kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="88f69-110">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="88f69-111">Například architektura pro sestavování grafického uživatelského rozhraní může poskytovat `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem.</span><span class="sxs-lookup"><span data-stu-id="88f69-111">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="88f69-112">Vzhledem k tomu, že jsou tyto členy interní, nejsou vystaveny kódu, který používá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="88f69-112">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="88f69-113">Jedná se o chybu, která odkazuje na typ nebo člen s vnitřním přístupem mimo sestavení, ve kterém byla definována.</span><span class="sxs-lookup"><span data-stu-id="88f69-113">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88f69-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="88f69-114">Example</span></span>  
 <span data-ttu-id="88f69-115">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly1_a.cs` .</span><span class="sxs-lookup"><span data-stu-id="88f69-115">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="88f69-116">První soubor obsahuje interní základní třídu `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="88f69-116">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="88f69-117">Při pokusu o vytvoření instance v druhém souboru `BaseClass` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="88f69-117">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="88f69-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="88f69-118">Example</span></span>  
 <span data-ttu-id="88f69-119">V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1, a změňte úroveň přístupnosti `BaseClass` na `public` .</span><span class="sxs-lookup"><span data-stu-id="88f69-119">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="88f69-120">Změňte také úroveň přístupnosti člena `intM` na `internal` .</span><span class="sxs-lookup"><span data-stu-id="88f69-120">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="88f69-121">V takovém případě můžete vytvořit instanci třídy, ale nemůžete získat přístup k internímu členu.</span><span class="sxs-lookup"><span data-stu-id="88f69-121">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="88f69-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88f69-122">C# Language Specification</span></span>  

<span data-ttu-id="88f69-123">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="88f69-123">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="88f69-124">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="88f69-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88f69-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="88f69-125">See also</span></span>

- [<span data-ttu-id="88f69-126">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88f69-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="88f69-127">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="88f69-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="88f69-128">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88f69-128">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="88f69-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="88f69-129">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="88f69-130">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="88f69-130">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="88f69-131">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="88f69-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="88f69-132">public</span><span class="sxs-lookup"><span data-stu-id="88f69-132">public</span></span>](./public.md)
- [<span data-ttu-id="88f69-133">private</span><span class="sxs-lookup"><span data-stu-id="88f69-133">private</span></span>](./private.md)
- [<span data-ttu-id="88f69-134">protected</span><span class="sxs-lookup"><span data-stu-id="88f69-134">protected</span></span>](./protected.md)
