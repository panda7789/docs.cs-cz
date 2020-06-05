---
title: Obnovení práce bez chyby
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400367"
---
# <a name="resume-without-error"></a><span data-ttu-id="c6b76-102">Obnovení práce bez chyby</span><span class="sxs-lookup"><span data-stu-id="c6b76-102">Resume without error</span></span>
<span data-ttu-id="c6b76-103">`Resume`Příkaz se objevil mimo kód pro zpracování chyb, nebo se kód přeskočí do obslužné rutiny chyb, i když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="c6b76-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6b76-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c6b76-104">To correct this error</span></span>  
  
1. <span data-ttu-id="c6b76-105">Přesuňte `Resume` příkaz do obslužné rutiny chyb nebo jej odstraňte.</span><span class="sxs-lookup"><span data-stu-id="c6b76-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="c6b76-106">K popiskům nelze v rámci procedur vyskytovat, proto v proceduře vyhledejte popisek, který identifikuje obslužnou rutinu chyby.</span><span class="sxs-lookup"><span data-stu-id="c6b76-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="c6b76-107">Pokud najdete duplicitní popisek zadaný jako cíl `GoTo` příkazu, který není `On Error GoTo` příkazem, změňte popisek řádku tak, aby souhlasil s jeho zamýšleným cílem.</span><span class="sxs-lookup"><span data-stu-id="c6b76-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b76-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6b76-108">See also</span></span>

- [<span data-ttu-id="c6b76-109">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="c6b76-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="c6b76-110">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="c6b76-110">On Error Statement</span></span>](../statements/on-error-statement.md)
