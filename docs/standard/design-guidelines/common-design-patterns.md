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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b2c25728903e4a193a15e6586fffe528ecb7c7e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="common-design-patterns"></a><span data-ttu-id="39b75-102">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="39b75-102">Common Design Patterns</span></span>
<span data-ttu-id="39b75-103">Existuje řada knih na softwaru vzory, vzor jazyky a antipatterns, které řeší velmi široký předmět vzory.</span><span class="sxs-lookup"><span data-stu-id="39b75-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="39b75-104">Proto tato kapitola obsahuje pokyny a diskuzi související s velmi omezená sada schémat, které se často používají v návrhu rozhraní API rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39b75-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39b75-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="39b75-105">In This Section</span></span>  
 [<span data-ttu-id="39b75-106">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="39b75-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="39b75-107">Vzor pro metodu Dispose</span><span class="sxs-lookup"><span data-stu-id="39b75-107">Dispose Pattern</span></span>](../../../docs/standard/design-guidelines/dispose-pattern.md)  
 <span data-ttu-id="39b75-108">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="39b75-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="39b75-109">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="39b75-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b75-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="39b75-110">See Also</span></span>  
 [<span data-ttu-id="39b75-111">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="39b75-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
