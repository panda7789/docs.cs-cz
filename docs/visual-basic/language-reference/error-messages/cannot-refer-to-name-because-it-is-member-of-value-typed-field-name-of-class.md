---
title: Na člena '<name>' nelze odkazovat, protože se jedná o člen pole typu hodnota '<name>' třídy '<classname>', jehož třídou Base je 'System.MarshalByRefObject'.
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: c29d3def2299dc1d7e3b084b3408b3f919addc63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279579"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a><span data-ttu-id="e3c89-102">Nemůže odkazovat na "\<název >" protože se jedná o člen pole typu hodnota '\<název > "' třídy\<classname >' obsahující 'System.MarshalByRefObject' jako základní třída</span><span class="sxs-lookup"><span data-stu-id="e3c89-102">Cannot refer to '\<name>' because it is a member of the value-typed field '\<name>' of class '\<classname>' which has 'System.MarshalByRefObject' as a base class</span></span>
<span data-ttu-id="e3c89-103">`System.MarshalByRefObject` Třída umožňuje aplikacím, které podporují vzdálený přístup k objektům přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="e3c89-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="e3c89-104">Typy musí dědit z `MarshalByRejectObject` třídy, pokud je typ použít přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="e3c89-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="e3c89-105">Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, ve kterém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="e3c89-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="e3c89-106">**ID chyby:** BC30310</span><span class="sxs-lookup"><span data-stu-id="e3c89-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3c89-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e3c89-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="e3c89-108">Zkontrolujte, abyste měli jistotu, že je člen, který se odkazuje na platný odkaz.</span><span class="sxs-lookup"><span data-stu-id="e3c89-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="e3c89-109">Explicitně kvalifikovat člena s `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e3c89-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3c89-110">See also</span></span>
- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="e3c89-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="e3c89-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
