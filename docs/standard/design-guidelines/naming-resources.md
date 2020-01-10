---
title: Prostředky pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709163"
---
# <a name="naming-resources"></a><span data-ttu-id="38a3c-102">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="38a3c-102">Naming Resources</span></span>
<span data-ttu-id="38a3c-103">Vzhledem k tomu, že lokalizovatelné prostředky mohou být odkazovány prostřednictvím určitých objektů, jako by se jednalo o vlastnosti, pokyny pro pojmenování prostředků jsou podobné pravidlům vlastností.</span><span class="sxs-lookup"><span data-stu-id="38a3c-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="38a3c-104">**✓ DO** použít PascalCasing v klíčů prostředku.</span><span class="sxs-lookup"><span data-stu-id="38a3c-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="38a3c-105">**✓ DO** zadat popisný místo krátké identifikátory.</span><span class="sxs-lookup"><span data-stu-id="38a3c-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="38a3c-106">**X DO NOT** používat klíčová slova jazyka hlavní jazyky CLR.</span><span class="sxs-lookup"><span data-stu-id="38a3c-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="38a3c-107">**✓ DO** použijte pouze alfanumerické znaky a podtržítka v pojmenování prostředky.</span><span class="sxs-lookup"><span data-stu-id="38a3c-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="38a3c-108">**✓ DO** použít následující konvence pro prostředků zprávy výjimek.</span><span class="sxs-lookup"><span data-stu-id="38a3c-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="38a3c-109">Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:</span><span class="sxs-lookup"><span data-stu-id="38a3c-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="38a3c-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="38a3c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="38a3c-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="38a3c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a3c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38a3c-112">See also</span></span>

- [<span data-ttu-id="38a3c-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="38a3c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="38a3c-114">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="38a3c-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
