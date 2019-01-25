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
ms.openlocfilehash: 5c86660574e9d12f646eed9d6d6397781cb9b9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685487"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="ec1e2-102">Me, My, MyBase a MyClass v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec1e2-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="ec1e2-103">`Me`, `My`, `MyBase`, a `MyClass` v jazyce Visual Basic mají podobné názvy, ale různým účelům.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="ec1e2-104">Toto téma popisuje všechny tyto entity, aby bylo možné odlišit.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="ec1e2-105">Mně</span><span class="sxs-lookup"><span data-stu-id="ec1e2-105">Me</span></span>  
 <span data-ttu-id="ec1e2-106">`Me` – Klíčové slovo poskytuje způsob, jak odkazovat na konkrétní instanci třídy nebo struktury, ve kterém právě spouští kód.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="ec1e2-107">`Me` se chová jako objektová proměnná nebo proměnná struktury odkaz na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="ec1e2-108">Pomocí `Me` je obzvláště užitečné pro předávání informací o aktuálně spuštěném instanci třídy nebo struktury do procedury v jiné třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="ec1e2-109">Předpokládejme například, že máte následující postup v modulu.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="ec1e2-110">Můžete volat tento postup a předejte aktuální instancí třídy <xref:System.Windows.Forms.Form> třídy jako argument pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="ec1e2-111">Moje</span><span class="sxs-lookup"><span data-stu-id="ec1e2-111">My</span></span>  
 <span data-ttu-id="ec1e2-112">`My` Funkce poskytuje jednoduché a intuitivní přístup k několika [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, povolení uživatele jazyka Visual Basic k interakci s počítačem, aplikace, nastavení, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="ec1e2-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="ec1e2-113">MyBase</span></span>  
 <span data-ttu-id="ec1e2-114">`MyBase` – Klíčové slovo se chová jako proměnná objektu odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="ec1e2-115">`MyBase` běžně se používá pro přístup ke členům základní třídy, přepsat nebo Stínovaný v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="ec1e2-116">`MyBase.New` umožňuje explicitně volat konstruktor základní třídy v konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="ec1e2-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="ec1e2-117">MyClass</span></span>  
 <span data-ttu-id="ec1e2-118">`MyClass` – Klíčové slovo se chová jako odkaz na aktuální instanci třídy, jak byly původně implementované proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="ec1e2-119">`MyClass` je podobný `Me`, ale všechna volání metody na něm zacházeno, jako kdyby byly metodu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="ec1e2-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1e2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec1e2-120">See also</span></span>
- [<span data-ttu-id="ec1e2-121">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="ec1e2-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
