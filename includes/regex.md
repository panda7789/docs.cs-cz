---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802845"
---

> [!WARNING]
> <span data-ttu-id="6c3ea-101">Při použití <xref:System.Text.RegularExpressions> ke zpracování nedůvěryhodného vstupu předejte časový limit.</span><span class="sxs-lookup"><span data-stu-id="6c3ea-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="6c3ea-102">Uživatel se zlými úmysly může poskytnout vstup pro `RegularExpressions` [útok DoS (Denial-of-Service](https://www.us-cert.gov/ncas/tips/ST04-015)).</span><span class="sxs-lookup"><span data-stu-id="6c3ea-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="6c3ea-103">Rozhraní API rozhraní ASP.NET Core Framework, která používají `RegularExpressions` předávat časový limit.</span><span class="sxs-lookup"><span data-stu-id="6c3ea-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>
