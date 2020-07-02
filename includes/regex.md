---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802845"
---

> [!WARNING]
> Při použití <xref:System.Text.RegularExpressions> ke zpracování nedůvěryhodného vstupu předejte časový limit. Uživatel se zlými úmysly může poskytnout vstup pro `RegularExpressions` [útok DoS (Denial-of-Service](https://www.us-cert.gov/ncas/tips/ST04-015)). Rozhraní API rozhraní ASP.NET Core Framework, která používají `RegularExpressions` předávat časový limit.
