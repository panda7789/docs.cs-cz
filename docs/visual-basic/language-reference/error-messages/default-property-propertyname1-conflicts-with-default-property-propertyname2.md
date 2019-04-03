---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: ab45278b2e1199282e3066c34828b9bda716e162
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813168"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="8fbc6-102">Výchozí vlastnost '\<propertyname1 >' je v konfliktu s výchozí vlastností '\<Název_vlastnosti2 >' v '\<classname > "a je třeba ji deklarovat 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="8fbc6-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="8fbc6-103">Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="8fbc6-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="8fbc6-104">V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8fbc6-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="8fbc6-105">Tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="8fbc6-105">This message is a warning.</span></span> <span data-ttu-id="8fbc6-106">`Shadows` předpokládá se ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fbc6-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="8fbc6-107">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8fbc6-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8fbc6-108">**ID chyby:** BC40007</span><span class="sxs-lookup"><span data-stu-id="8fbc6-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8fbc6-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8fbc6-109">To correct this error</span></span>  
  
-   <span data-ttu-id="8fbc6-110">Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.</span><span class="sxs-lookup"><span data-stu-id="8fbc6-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbc6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fbc6-111">See also</span></span>

- [<span data-ttu-id="8fbc6-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="8fbc6-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="8fbc6-113">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fbc6-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
