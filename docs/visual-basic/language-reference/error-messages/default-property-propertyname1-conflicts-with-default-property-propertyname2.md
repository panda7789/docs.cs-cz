---
title: "Výchozí vlastnost & č. 39; &lt;propertyname1&gt;& č. 39; je v konfliktu s výchozí vlastnost & č. 39;&lt; Název_vlastnosti2&gt;& č. 39; v & č. 39;&lt; Název třídy&gt;& č. 39; a proto musí být deklarován & č. 39; Stínů & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords: BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="116c8-102">Výchozí vlastnost & č. 39; &lt;propertyname1&gt;& č. 39; je v konfliktu s výchozí vlastnost & č. 39;&lt; Název_vlastnosti2&gt;& č. 39; v & č. 39;&lt; Název třídy&gt;& č. 39; a proto musí být deklarován & č. 39; Stínů & č. 39;</span><span class="sxs-lookup"><span data-stu-id="116c8-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="116c8-103">Vlastnost je deklarován se stejným názvem jako vlastnost definovanou v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="116c8-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="116c8-104">V takovém případě by měl stínové vlastnost v této třídě vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="116c8-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="116c8-105">Tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="116c8-105">This message is a warning.</span></span> <span data-ttu-id="116c8-106">`Shadows`ve výchozím nastavení se předpokládá.</span><span class="sxs-lookup"><span data-stu-id="116c8-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="116c8-107">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="116c8-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="116c8-108">**ID chyby:** BC40007</span><span class="sxs-lookup"><span data-stu-id="116c8-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="116c8-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="116c8-109">To correct this error</span></span>  
  
-   <span data-ttu-id="116c8-110">Přidat `Shadows` – klíčové slovo na deklaraci nebo změňte název vlastnosti je deklarován.</span><span class="sxs-lookup"><span data-stu-id="116c8-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116c8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="116c8-111">See Also</span></span>  
 [<span data-ttu-id="116c8-112">Stínů</span><span class="sxs-lookup"><span data-stu-id="116c8-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="116c8-113">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="116c8-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
