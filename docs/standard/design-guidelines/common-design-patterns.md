---
title: Obecné vzory návrhu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
ms.openlocfilehash: 2c51b1c9bc970d6ff143fa5986eade4a8b69f25a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709501"
---
# <a name="common-design-patterns"></a><span data-ttu-id="b2629-102">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="b2629-102">Common Design Patterns</span></span>
<span data-ttu-id="b2629-103">K dispozici je mnoho knih o vzorech softwaru, jazycích vzorů a antipatternech, které řeší velmi široké téma vzorů.</span><span class="sxs-lookup"><span data-stu-id="b2629-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="b2629-104">Proto tato kapitola poskytuje pokyny a diskuzi týkající se velmi omezené sady vzorů, které se často používají v návrhu .NET Framework rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b2629-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2629-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b2629-105">In This Section</span></span>  
 [<span data-ttu-id="b2629-106">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="b2629-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="b2629-107">Vzor pro metodu Dispose</span><span class="sxs-lookup"><span data-stu-id="b2629-107">Dispose Pattern</span></span>](../garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="b2629-108">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="b2629-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b2629-109">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="b2629-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2629-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2629-110">See also</span></span>

- [<span data-ttu-id="b2629-111">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="b2629-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
