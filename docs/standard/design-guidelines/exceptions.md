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
ms.openlocfilehash: b64b6052aeb99c6e878c1a9aac50e67bca7f8d2a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709371"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="e2d1a-102">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="e2d1a-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="e2d1a-103">Zpracování výjimek má mnoho výhod pro zasílání zpráv o chybách na základě návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="e2d1a-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="e2d1a-104">Dobrý návrh rozhraní pomáhá vývojářům aplikace využít výhody výjimek.</span><span class="sxs-lookup"><span data-stu-id="e2d1a-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="e2d1a-105">Tato část popisuje výhody výjimek a prezentuje pokyny pro jejich efektivní použití.</span><span class="sxs-lookup"><span data-stu-id="e2d1a-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2d1a-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e2d1a-106">In This Section</span></span>  
 [<span data-ttu-id="e2d1a-107">Vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="e2d1a-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="e2d1a-108">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="e2d1a-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="e2d1a-109">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="e2d1a-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="e2d1a-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e2d1a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e2d1a-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="e2d1a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d1a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2d1a-112">See also</span></span>

- [<span data-ttu-id="e2d1a-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="e2d1a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
