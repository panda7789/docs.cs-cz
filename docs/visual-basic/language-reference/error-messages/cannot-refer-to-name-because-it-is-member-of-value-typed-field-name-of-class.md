---
title: Nemůže odkazovat na &#39; &lt;název&gt; &#39; protože je členem pole zadali hodnotu &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;jehož &#39;System.MarshalByRefObject&#39; jako základní třída
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586344"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="0a0c4-102">Nemůže odkazovat na &#39; &lt;název&gt; &#39; protože je členem pole zadali hodnotu &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;jehož &#39;System.MarshalByRefObject&#39; jako základní třída</span><span class="sxs-lookup"><span data-stu-id="0a0c4-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="0a0c4-103">`System.MarshalByRefObject` – Třída umožňuje aplikacím, které podporují vzdáleného přístupu k objektům napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a0c4-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="0a0c4-104">Typy musí dědit z `MarshalByRejectObject` třídy, pokud typ se používá napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a0c4-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="0a0c4-105">Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, v jakém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="0a0c4-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="0a0c4-106">**ID chyby:** BC30310</span><span class="sxs-lookup"><span data-stu-id="0a0c4-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a0c4-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0a0c4-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0a0c4-108">Zkontrolujte odkaz na zkontrolujte, zda člen odkazovaného je platný.</span><span class="sxs-lookup"><span data-stu-id="0a0c4-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="0a0c4-109">Explicitně kvalifikaci člena s `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0a0c4-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0c4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a0c4-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="0a0c4-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="0a0c4-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
