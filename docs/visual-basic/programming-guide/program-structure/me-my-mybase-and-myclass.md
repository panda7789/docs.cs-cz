---
title: Me, My, MyBase a MyClass v jazyce Visual Basic
ms.date: 07/20/2015
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
ms.openlocfilehash: 7df146e09a1d7cd730f4cf539d6823f7ced44bd1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002529"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="23935-102">Me, My, MyBase a MyClass v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23935-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="23935-103">`Me`, `My`, `MyBase` a `MyClass` v Visual Basic mají podobné názvy, ale různé účely.</span><span class="sxs-lookup"><span data-stu-id="23935-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="23935-104">Toto téma popisuje každou z těchto entit, aby je bylo možné odlišit.</span><span class="sxs-lookup"><span data-stu-id="23935-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="23935-105">Mně</span><span class="sxs-lookup"><span data-stu-id="23935-105">Me</span></span>  
 <span data-ttu-id="23935-106">Klíčové slovo `Me` poskytuje způsob, jak odkazovat na konkrétní instanci třídy nebo struktury, ve které je kód aktuálně spuštěn.</span><span class="sxs-lookup"><span data-stu-id="23935-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="23935-107">`Me` se chová jako proměnná objektu nebo proměnná struktury odkazující na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="23935-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="23935-108">Použití `Me` je zvlášť užitečné pro předávání informací o aktuálně vykonávané instanci třídy nebo struktury na proceduru v jiné třídě, struktuře nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="23935-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="23935-109">Předpokládejme například, že v modulu máte následující proceduru.</span><span class="sxs-lookup"><span data-stu-id="23935-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="23935-110">Tento postup můžete zavolat a předat aktuální instanci třídy <xref:System.Windows.Forms.Form> jako argument pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="23935-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="23935-111">Moje</span><span class="sxs-lookup"><span data-stu-id="23935-111">My</span></span>  
 <span data-ttu-id="23935-112">Funkce `My` poskytuje snadný a intuitivní přístup k řadě tříd .NET Framework a umožňuje uživatelům Visual Basic interakci s počítačem, aplikací, nastavením, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="23935-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="23935-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="23935-113">MyBase</span></span>  
 <span data-ttu-id="23935-114">Klíčové slovo `MyBase` se chová jako proměnná objektu odkazující na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="23935-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="23935-115">`MyBase` se běžně používá pro přístup ke členům základních tříd, které jsou přepsány nebo vrženy v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="23935-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="23935-116">`MyBase.New` slouží k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="23935-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="23935-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="23935-117">MyClass</span></span>  
 <span data-ttu-id="23935-118">Klíčové slovo `MyClass` se chová jako proměnná objektu odkazující na aktuální instanci třídy, jak je původně implementována.</span><span class="sxs-lookup"><span data-stu-id="23935-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="23935-119">`MyClass` je podobný `Me`, ale všechna volání metody jsou považována za, jako kdyby byla metoda `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="23935-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23935-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23935-120">See also</span></span>

- [<span data-ttu-id="23935-121">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="23935-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
