---
title: Obecné vzory návrhu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
ms.openlocfilehash: 9b9525a7597f7df6c9a554b51160a99f0e06232c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290964"
---
# <a name="common-design-patterns"></a><span data-ttu-id="95b4e-102">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="95b4e-102">Common Design Patterns</span></span>
<span data-ttu-id="95b4e-103">K dispozici je mnoho knih o vzorech softwaru, jazycích vzorů a antipatternech, které řeší velmi široké téma vzorů.</span><span class="sxs-lookup"><span data-stu-id="95b4e-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="95b4e-104">Proto tato kapitola poskytuje pokyny a diskuzi týkající se velmi omezené sady vzorů, které se často používají v návrhu .NET Framework rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="95b4e-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95b4e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="95b4e-105">In This Section</span></span>  
 [<span data-ttu-id="95b4e-106">Vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="95b4e-106">Dependency Properties</span></span>](dependency-properties.md)  
 [<span data-ttu-id="95b4e-107">Vzor pro metodu Dispose</span><span class="sxs-lookup"><span data-stu-id="95b4e-107">Dispose Pattern</span></span>](../garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="95b4e-108">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="95b4e-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="95b4e-109">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="95b4e-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b4e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="95b4e-110">See also</span></span>

- [<span data-ttu-id="95b4e-111">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="95b4e-111">Framework Design Guidelines</span></span>](index.md)
