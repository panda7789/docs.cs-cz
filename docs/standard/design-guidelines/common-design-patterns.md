---
title: "Obecné vzory návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d78e675ebc67cc2e49f5bc7141558d462a3e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="common-design-patterns"></a><span data-ttu-id="1b0b8-102">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="1b0b8-102">Common Design Patterns</span></span>
<span data-ttu-id="1b0b8-103">Existuje řada knih na softwaru vzory, vzor jazyky a antipatterns, které řeší velmi široký předmět vzory.</span><span class="sxs-lookup"><span data-stu-id="1b0b8-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="1b0b8-104">Proto tato kapitola obsahuje pokyny a diskuzi související s velmi omezená sada schémat, které se často používají v návrhu rozhraní API rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b0b8-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b0b8-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1b0b8-105">In This Section</span></span>  
 [<span data-ttu-id="1b0b8-106">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="1b0b8-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="1b0b8-107">Dispose – vzor</span><span class="sxs-lookup"><span data-stu-id="1b0b8-107">Dispose Pattern</span></span>](../../../docs/standard/design-guidelines/dispose-pattern.md)  
 <span data-ttu-id="1b0b8-108">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="1b0b8-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1b0b8-109">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1b0b8-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0b8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b0b8-110">See Also</span></span>  
 [<span data-ttu-id="1b0b8-111">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="1b0b8-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
