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
ms.openlocfilehash: 95aff35569e58eacfd064609140a29b53e0036da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743811"
---
# <a name="naming-resources"></a><span data-ttu-id="b3c13-102">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="b3c13-102">Naming Resources</span></span>
<span data-ttu-id="b3c13-103">Vzhledem k tomu, že lokalizovatelné prostředky mohou být odkazovány prostřednictvím určitých objektů, jako by se jednalo o vlastnosti, pokyny pro pojmenování prostředků jsou podobné pravidlům vlastností.</span><span class="sxs-lookup"><span data-stu-id="b3c13-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="b3c13-104">✔️ používat PascalCasing v klíčích prostředků.</span><span class="sxs-lookup"><span data-stu-id="b3c13-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="b3c13-105">✔️ Zadejte popisný název místo krátkých identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="b3c13-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="b3c13-106">❌ pro hlavní jazyky CLR nepoužívejte klíčová slova specifická pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="b3c13-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="b3c13-107">✔️ v názvech prostředků používat pouze alfanumerické znaky a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="b3c13-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="b3c13-108">✔️ použít následující zásady vytváření názvů pro prostředky zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="b3c13-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="b3c13-109">Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:</span><span class="sxs-lookup"><span data-stu-id="b3c13-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="b3c13-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="b3c13-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="b3c13-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="b3c13-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b3c13-112">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="b3c13-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c13-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3c13-113">See also</span></span>

- [<span data-ttu-id="b3c13-114">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="b3c13-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b3c13-115">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="b3c13-115">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
