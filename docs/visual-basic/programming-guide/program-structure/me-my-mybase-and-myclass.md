---
title: Me, My, MyBase a MyClass v jazyce Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="372ed-102">Me, My, MyBase a MyClass v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="372ed-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="372ed-103">`Me`, `My`, `MyBase`, a `MyClass` v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] mají podobné názvy, ale jiné účely.</span><span class="sxs-lookup"><span data-stu-id="372ed-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="372ed-104">Toto téma popisuje každou z těchto položek, aby bylo možné odlišit.</span><span class="sxs-lookup"><span data-stu-id="372ed-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="372ed-105">Mně</span><span class="sxs-lookup"><span data-stu-id="372ed-105">Me</span></span>  
 <span data-ttu-id="372ed-106">`Me` – Klíčové slovo poskytuje způsob, jak odkazovat na konkrétní instanci třídu nebo strukturu, ve kterém je aktuálně provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="372ed-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="372ed-107">`Me`chová jako objektová proměnná nebo proměnná struktura odkaz na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="372ed-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="372ed-108">Pomocí `Me` je zvláště užitečná pro předávání informací o aktuálně spuštěném instanci třídu nebo strukturu proceduře v jiné třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="372ed-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="372ed-109">Předpokládejme například, že máte následující postup v modulu.</span><span class="sxs-lookup"><span data-stu-id="372ed-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="372ed-110">Můžete tento postup a předejte aktuální instancí třídy <xref:System.Windows.Forms.Form> třída jako argument pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="372ed-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="372ed-111">Moje</span><span class="sxs-lookup"><span data-stu-id="372ed-111">My</span></span>  
 <span data-ttu-id="372ed-112">`My` Funkce poskytuje snadný a intuitivní přístup k několika [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, povolení [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uživatelům interakci s počítači, aplikace, nastavení, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="372ed-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="372ed-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="372ed-113">MyBase</span></span>  
 <span data-ttu-id="372ed-114">`MyBase` – Klíčové slovo chová jako proměnná objektu odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="372ed-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="372ed-115">`MyBase`se běžně používá pro přístup k členy základní třídy, které jsou přepsat nebo Stínovaný v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="372ed-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="372ed-116">`MyBase.New`slouží k explicitně volání konstruktoru základní třídy z konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="372ed-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="372ed-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="372ed-117">MyClass</span></span>  
 <span data-ttu-id="372ed-118">`MyClass` – Klíčové slovo chová jako odkaz na aktuální instanci třídy jako poprvé implementované proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="372ed-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="372ed-119">`MyClass`je podobná `Me`, ale všechny volání metod v něm jsou zpracovány jako kdyby metodu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="372ed-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372ed-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="372ed-120">See Also</span></span>  
 [<span data-ttu-id="372ed-121">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="372ed-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
