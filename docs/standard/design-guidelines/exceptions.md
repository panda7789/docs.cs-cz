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
ms.openlocfilehash: d7580d4d3953b279824bba76b44c4134a7293b7a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289769"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="c9751-102">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="c9751-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="c9751-103">Zpracování výjimek má mnoho výhod pro zasílání zpráv o chybách na základě návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="c9751-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="c9751-104">Dobrý návrh rozhraní pomáhá vývojářům aplikace využít výhody výjimek.</span><span class="sxs-lookup"><span data-stu-id="c9751-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="c9751-105">Tato část popisuje výhody výjimek a prezentuje pokyny pro jejich efektivní použití.</span><span class="sxs-lookup"><span data-stu-id="c9751-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9751-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c9751-106">In This Section</span></span>  
 [<span data-ttu-id="c9751-107">Vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="c9751-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="c9751-108">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="c9751-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="c9751-109">Výjimky a výkon</span><span class="sxs-lookup"><span data-stu-id="c9751-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="c9751-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="c9751-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c9751-111">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="c9751-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9751-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9751-112">See also</span></span>

- [<span data-ttu-id="c9751-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="c9751-113">Framework Design Guidelines</span></span>](index.md)
