---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: bc75b01532ffb112622d7f9bc837490c627883b3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270381"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="2da0c-102">Výchozí vlastnost '\<propertyname1 >' je v konfliktu s výchozí vlastností '\<Název_vlastnosti2 >' v '\<classname > "a je třeba ji deklarovat 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="2da0c-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="2da0c-103">Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="2da0c-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="2da0c-104">V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2da0c-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="2da0c-105">Tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="2da0c-105">This message is a warning.</span></span> <span data-ttu-id="2da0c-106">`Shadows` předpokládá se ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2da0c-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="2da0c-107">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2da0c-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2da0c-108">**ID chyby:** BC40007</span><span class="sxs-lookup"><span data-stu-id="2da0c-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2da0c-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2da0c-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2da0c-110">Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.</span><span class="sxs-lookup"><span data-stu-id="2da0c-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da0c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2da0c-111">See also</span></span>
- [<span data-ttu-id="2da0c-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="2da0c-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2da0c-113">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da0c-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
