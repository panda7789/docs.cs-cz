---
title: Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastností &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a je třeba ji deklarovat &#39;stíny&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521423"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="fe6bc-102">Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastností &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a je třeba ji deklarovat &#39;stíny&#39;</span><span class="sxs-lookup"><span data-stu-id="fe6bc-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="fe6bc-103">Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="fe6bc-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="fe6bc-104">V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fe6bc-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="fe6bc-105">Tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="fe6bc-105">This message is a warning.</span></span> <span data-ttu-id="fe6bc-106">`Shadows` předpokládá se ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="fe6bc-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="fe6bc-107">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fe6bc-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fe6bc-108">**ID chyby:** BC40007</span><span class="sxs-lookup"><span data-stu-id="fe6bc-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fe6bc-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fe6bc-109">To correct this error</span></span>  
  
-   <span data-ttu-id="fe6bc-110">Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.</span><span class="sxs-lookup"><span data-stu-id="fe6bc-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6bc-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe6bc-111">See also</span></span>
- [<span data-ttu-id="fe6bc-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="fe6bc-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="fe6bc-113">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe6bc-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
