---
title: interní – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173598"
---
# <a name="internal-c-reference"></a><span data-ttu-id="61312-102">internal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="61312-102">internal (C# Reference)</span></span>
<span data-ttu-id="61312-103">Klíčové `internal` slovo je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="61312-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="61312-104">Tato stránka `internal` se týká přístupu.</span><span class="sxs-lookup"><span data-stu-id="61312-104">This page covers `internal` access.</span></span> <span data-ttu-id="61312-105">Klíčové `internal` slovo je také [`protected internal`](./protected-internal.md) součástí modifikátoru přístupu.</span><span class="sxs-lookup"><span data-stu-id="61312-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="61312-106">Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="61312-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="61312-107">Porovnání s `internal` ostatními modifikátory přístupu naleznete v [tématu Úrovně přístupnosti](./accessibility-levels.md) a [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="61312-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="61312-108">Další informace o sestaveních naleznete [v tématu Sestavení v rozhraní .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="61312-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="61312-109">Běžné použití interního přístupu je ve vývoji založeném na součástech, protože umožňuje skupině součástí spolupracovat soukromým způsobem, aniž by byla vystavena zbytku kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="61312-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="61312-110">Například rámec pro vytváření grafických uživatelských rozhraní může poskytnout `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem.</span><span class="sxs-lookup"><span data-stu-id="61312-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="61312-111">Vzhledem k tomu, že tyto členy jsou interní, nejsou vystaveny kódu, který používá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="61312-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="61312-112">Je chyba odkazovat na typ nebo člen s internípřístup mimo sestavení, ve kterém byl definován.</span><span class="sxs-lookup"><span data-stu-id="61312-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61312-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="61312-113">Example</span></span>  
 <span data-ttu-id="61312-114">Tento příklad obsahuje `Assembly1.cs` dva `Assembly1_a.cs`soubory a .</span><span class="sxs-lookup"><span data-stu-id="61312-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="61312-115">První soubor obsahuje vnitřní základní `BaseClass`třídu .</span><span class="sxs-lookup"><span data-stu-id="61312-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="61312-116">V druhém souboru dojde k vytvoření `BaseClass` instance.</span><span class="sxs-lookup"><span data-stu-id="61312-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="61312-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="61312-117">Example</span></span>  
 <span data-ttu-id="61312-118">V tomto příkladu použijte stejné soubory, které jste použili `BaseClass` `public`v příkladu 1, a změňte úroveň usnadnění na .</span><span class="sxs-lookup"><span data-stu-id="61312-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="61312-119">Změňte také úroveň usnadnění `intM` `internal`přístupu člena na .</span><span class="sxs-lookup"><span data-stu-id="61312-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="61312-120">V takovém případě můžete vytvořit instanci třídy, ale nelze získat přístup k interní člen.</span><span class="sxs-lookup"><span data-stu-id="61312-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="61312-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61312-121">C# Language Specification</span></span>  

<span data-ttu-id="61312-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="61312-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="61312-123">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="61312-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="61312-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="61312-124">See also</span></span>

- [<span data-ttu-id="61312-125">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61312-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="61312-126">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61312-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="61312-127">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="61312-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="61312-128">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="61312-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="61312-129">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="61312-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="61312-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="61312-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="61312-131">Veřejné</span><span class="sxs-lookup"><span data-stu-id="61312-131">public</span></span>](./public.md)
- [<span data-ttu-id="61312-132">Soukromé</span><span class="sxs-lookup"><span data-stu-id="61312-132">private</span></span>](./private.md)
- [<span data-ttu-id="61312-133">protected</span><span class="sxs-lookup"><span data-stu-id="61312-133">protected</span></span>](./protected.md)
