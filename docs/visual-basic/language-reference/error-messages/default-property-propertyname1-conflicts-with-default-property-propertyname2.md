---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409722"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="f3092-102">Výchozí vlastnost '\<propertyname1>' je v konfliktu s výchozí vlastností '\<propertyname2>' ve třídě '\<classname>' a je ji třeba deklarovat jako 'Shadows'.</span><span class="sxs-lookup"><span data-stu-id="f3092-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="f3092-103">Vlastnost je deklarována se stejným názvem jako vlastnost definovaná v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="f3092-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="f3092-104">V této situaci by vlastnost v této třídě měla vytvořit stínovou vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f3092-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="f3092-105">Tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="f3092-105">This message is a warning.</span></span> <span data-ttu-id="f3092-106">`Shadows`je ve výchozím nastavení předpokládaná.</span><span class="sxs-lookup"><span data-stu-id="f3092-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="f3092-107">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f3092-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f3092-108">**ID chyby:** BC40007</span><span class="sxs-lookup"><span data-stu-id="f3092-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3092-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f3092-109">To correct this error</span></span>  
  
- <span data-ttu-id="f3092-110">Přidejte `Shadows` klíčové slovo do deklarace nebo změňte název vlastnosti, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="f3092-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3092-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3092-111">See also</span></span>

- [<span data-ttu-id="f3092-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="f3092-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="f3092-113">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3092-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
