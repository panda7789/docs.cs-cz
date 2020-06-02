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
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290146"
---
# <a name="naming-resources"></a><span data-ttu-id="99b22-102">Prostředky pojmenování</span><span class="sxs-lookup"><span data-stu-id="99b22-102">Naming Resources</span></span>
<span data-ttu-id="99b22-103">Vzhledem k tomu, že lokalizovatelné prostředky mohou být odkazovány prostřednictvím určitých objektů, jako by se jednalo o vlastnosti, pokyny pro pojmenování prostředků jsou podobné pravidlům vlastností.</span><span class="sxs-lookup"><span data-stu-id="99b22-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="99b22-104">✔️ používat PascalCasing v klíčích prostředků.</span><span class="sxs-lookup"><span data-stu-id="99b22-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="99b22-105">✔️ Zadejte popisný název místo krátkých identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="99b22-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="99b22-106">❌Nepoužívejte klíčová slova specifická pro jazyky modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="99b22-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="99b22-107">✔️ v názvech prostředků používat pouze alfanumerické znaky a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="99b22-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="99b22-108">✔️ použít následující zásady vytváření názvů pro prostředky zpráv o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="99b22-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="99b22-109">Identifikátor prostředku by měl být název typu výjimky a krátký identifikátor výjimky:</span><span class="sxs-lookup"><span data-stu-id="99b22-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="99b22-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="99b22-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="99b22-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="99b22-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="99b22-112">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="99b22-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="99b22-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="99b22-113">See also</span></span>

- [<span data-ttu-id="99b22-114">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="99b22-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="99b22-115">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="99b22-115">Naming Guidelines</span></span>](naming-guidelines.md)
