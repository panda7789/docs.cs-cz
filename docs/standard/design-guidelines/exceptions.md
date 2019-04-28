---
title: Pokyny k návrhu pro výjimky
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: KrzysztofCwalina
ms.openlocfilehash: 60c3d25138c224f5eabf44d06b6c9a8373eb5f96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669046"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="cea7f-102">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="cea7f-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="cea7f-103">Zpracování výjimek má mnoho výhod oproti hlášení chyb na základě vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cea7f-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="cea7f-104">Návrh dobrý framework pomáhá vývojář aplikace začít využívat výhod výjimky.</span><span class="sxs-lookup"><span data-stu-id="cea7f-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="cea7f-105">Tato část vás seznámí s výhodami výjimky a zobrazí pokyny pro jejich efektivní využití.</span><span class="sxs-lookup"><span data-stu-id="cea7f-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cea7f-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cea7f-106">In This Section</span></span>  
 [<span data-ttu-id="cea7f-107">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="cea7f-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="cea7f-108">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="cea7f-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="cea7f-109">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="cea7f-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="cea7f-110">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="cea7f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cea7f-111">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="cea7f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea7f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cea7f-112">See also</span></span>

- [<span data-ttu-id="cea7f-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="cea7f-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
