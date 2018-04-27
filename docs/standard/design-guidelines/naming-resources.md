---
title: Názvy prostředků
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b100366952b1f536d187eb72c6d80c86bb3e572e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="naming-resources"></a><span data-ttu-id="2afd3-102">Názvy prostředků</span><span class="sxs-lookup"><span data-stu-id="2afd3-102">Naming Resources</span></span>
<span data-ttu-id="2afd3-103">Protože lokalizovatelný prostředků může být odkazováno prostřednictvím určité objekty, jako kdyby byly vlastnosti, jsou podobné vlastnost pokyny pro pojmenování pokyny pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="2afd3-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="2afd3-104">**PROVEĎTE ✓** použít PascalCasing v klíčů prostředku.</span><span class="sxs-lookup"><span data-stu-id="2afd3-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="2afd3-105">**PROVEĎTE ✓** zadat popisný místo krátké identifikátory.</span><span class="sxs-lookup"><span data-stu-id="2afd3-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="2afd3-106">**X nesmí** používat klíčová slova jazyka hlavní jazyky CLR.</span><span class="sxs-lookup"><span data-stu-id="2afd3-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="2afd3-107">**PROVEĎTE ✓** použijte pouze alfanumerické znaky a podtržítka v pojmenování prostředky.</span><span class="sxs-lookup"><span data-stu-id="2afd3-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="2afd3-108">**PROVEĎTE ✓** použít následující konvence pro prostředků zprávy výjimek.</span><span class="sxs-lookup"><span data-stu-id="2afd3-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="2afd3-109">Identifikátor prostředku musí být název typu výjimka plus krátké identifikátor výjimky:</span><span class="sxs-lookup"><span data-stu-id="2afd3-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="2afd3-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="2afd3-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2afd3-111">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2afd3-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afd3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2afd3-112">See Also</span></span>  
 [<span data-ttu-id="2afd3-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="2afd3-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="2afd3-114">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="2afd3-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
