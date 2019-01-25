---
title: Nelze odkazovat na &#39; &lt;název&gt; &#39; protože se jedná o člen pole typu hodnota &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;obsahující &#39;System.MarshalByRefObject&#39; jako základní třída
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739294"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="c638d-102">Nelze odkazovat na &#39; &lt;název&gt; &#39; protože se jedná o člen pole typu hodnota &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;obsahující &#39;System.MarshalByRefObject&#39; jako základní třída</span><span class="sxs-lookup"><span data-stu-id="c638d-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="c638d-103">`System.MarshalByRefObject` Třída umožňuje aplikacím, které podporují vzdálený přístup k objektům přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="c638d-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="c638d-104">Typy musí dědit z `MarshalByRejectObject` třídy, pokud je typ použít přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="c638d-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="c638d-105">Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, ve kterém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="c638d-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="c638d-106">**ID chyby:** BC30310</span><span class="sxs-lookup"><span data-stu-id="c638d-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c638d-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c638d-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c638d-108">Zkontrolujte, abyste měli jistotu, že je člen, který se odkazuje na platný odkaz.</span><span class="sxs-lookup"><span data-stu-id="c638d-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="c638d-109">Explicitně kvalifikovat člena s `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c638d-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c638d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c638d-110">See also</span></span>
- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="c638d-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="c638d-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
