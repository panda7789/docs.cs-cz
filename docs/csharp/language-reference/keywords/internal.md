---
title: interní C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 7d97b7b05645b02a31af848c97758c7a1f6423b9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602084"
---
# <a name="internal-c-reference"></a><span data-ttu-id="f5eb9-102">internal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f5eb9-102">internal (C# Reference)</span></span>
<span data-ttu-id="f5eb9-103">Klíčové slovo je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typů. `internal`</span><span class="sxs-lookup"><span data-stu-id="f5eb9-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="f5eb9-104">Tato stránka se `internal` zabývá přístupem.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-104">This page covers `internal` access.</span></span> <span data-ttu-id="f5eb9-105">Klíčové slovo je také součástí [`protected internal`](./protected-internal.md) modifikátoru přístupu. `internal`</span><span class="sxs-lookup"><span data-stu-id="f5eb9-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="f5eb9-106">Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="f5eb9-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="f5eb9-107">Porovnání `internal` s dalšími modifikátory přístupu najdete v tématu [úrovně](./accessibility-levels.md) přístupnosti a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f5eb9-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f5eb9-108">Další informace o sestaveních naleznete [v tématu sestavení v rozhraní .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5eb9-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="f5eb9-109">Běžné použití interního přístupu je v rámci vývoje založeného na komponentách, protože umožňuje skupině komponent, aby spolupracovaly soukromě, aniž by bylo zveřejněno pro zbytek kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="f5eb9-110">Například architektura pro sestavování grafického uživatelského rozhraní může poskytovat `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="f5eb9-111">Vzhledem k tomu, že jsou tyto členy interní, nejsou vystaveny kódu, který používá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="f5eb9-112">Jedná se o chybu, která odkazuje na typ nebo člen s vnitřním přístupem mimo sestavení, ve kterém byla definována.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5eb9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5eb9-113">Example</span></span>  
 <span data-ttu-id="f5eb9-114">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="f5eb9-115">První soubor obsahuje interní základní třídu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="f5eb9-116">Při pokusu o vytvoření instance `BaseClass` v druhém souboru dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f5eb9-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5eb9-117">Example</span></span>  
 <span data-ttu-id="f5eb9-118">V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1, a změňte úroveň `BaseClass` přístupnosti na. `public`</span><span class="sxs-lookup"><span data-stu-id="f5eb9-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="f5eb9-119">Změňte také úroveň přístupnosti člena `intM` na. `internal`</span><span class="sxs-lookup"><span data-stu-id="f5eb9-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="f5eb9-120">V takovém případě můžete vytvořit instanci třídy, ale nemůžete získat přístup k internímu členu.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="f5eb9-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f5eb9-121">C# Language Specification</span></span>  

<span data-ttu-id="f5eb9-122">Další informace najdete v tématu [deklarované](~/_csharplang/spec/basic-concepts.md#declared-accessibility) přístupnosti ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5eb9-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="f5eb9-123">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f5eb9-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5eb9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5eb9-124">See also</span></span>

- [<span data-ttu-id="f5eb9-125">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="f5eb9-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5eb9-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f5eb9-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5eb9-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f5eb9-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f5eb9-128">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="f5eb9-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="f5eb9-129">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="f5eb9-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="f5eb9-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="f5eb9-130">Modifiers</span></span>](./modifiers.md)
- [<span data-ttu-id="f5eb9-131">public</span><span class="sxs-lookup"><span data-stu-id="f5eb9-131">public</span></span>](./public.md)
- [<span data-ttu-id="f5eb9-132">private</span><span class="sxs-lookup"><span data-stu-id="f5eb9-132">private</span></span>](./private.md)
- [<span data-ttu-id="f5eb9-133">protected</span><span class="sxs-lookup"><span data-stu-id="f5eb9-133">protected</span></span>](./protected.md)
