---
title: "Nemůže odkazovat na & č. 39; &lt;název&gt;& č. 39; protože je členem pole zadali hodnotu & č. 39;&lt; název&gt;& č. 39; třída & č. 39;&lt; Název třídy&gt;& č. 39; který má & č. 39; System.MarshalByRefObject & č. 39; jako základní třída"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords: BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="b0cef-102">Nemůže odkazovat na & č. 39; &lt;název&gt;& č. 39; protože je členem pole zadali hodnotu & č. 39;&lt; název&gt;& č. 39; třída & č. 39;&lt; Název třídy&gt;& č. 39; který má & č. 39; System.MarshalByRefObject & č. 39; jako základní třída</span><span class="sxs-lookup"><span data-stu-id="b0cef-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="b0cef-103">`System.MarshalByRefObject` – Třída umožňuje aplikacím, které podporují vzdáleného přístupu k objektům napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0cef-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="b0cef-104">Typy musí dědit z `MarshalByRejectObject` třídy, pokud typ se používá napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0cef-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="b0cef-105">Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, v jakém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="b0cef-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="b0cef-106">**ID chyby:** BC30310</span><span class="sxs-lookup"><span data-stu-id="b0cef-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0cef-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0cef-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b0cef-108">Zkontrolujte odkaz na zkontrolujte, zda člen odkazovaného je platný.</span><span class="sxs-lookup"><span data-stu-id="b0cef-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="b0cef-109">Explicitně kvalifikaci člena s `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b0cef-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cef-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0cef-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="b0cef-111">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0cef-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
