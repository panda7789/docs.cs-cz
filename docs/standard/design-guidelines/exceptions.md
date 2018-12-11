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
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153189"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="9f936-102">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="9f936-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="9f936-103">Zpracování výjimek má mnoho výhod oproti hlášení chyb na základě vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f936-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="9f936-104">Návrh dobrý framework pomáhá vývojář aplikace začít využívat výhod výjimky.</span><span class="sxs-lookup"><span data-stu-id="9f936-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="9f936-105">Tato část vás seznámí s výhodami výjimky a zobrazí pokyny pro jejich efektivní využití.</span><span class="sxs-lookup"><span data-stu-id="9f936-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f936-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9f936-106">In This Section</span></span>  
 [<span data-ttu-id="9f936-107">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="9f936-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="9f936-108">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="9f936-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="9f936-109">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="9f936-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="9f936-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9f936-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9f936-111">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="9f936-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f936-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f936-112">See also</span></span>

- [<span data-ttu-id="9f936-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9f936-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
