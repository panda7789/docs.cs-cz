---
title: Obnovení práce bez chyby
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 61332486b20af66af24eac06b222a38353578c16
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300902"
---
# <a name="resume-without-error"></a><span data-ttu-id="3114a-102">Obnovení práce bez chyby</span><span class="sxs-lookup"><span data-stu-id="3114a-102">Resume without error</span></span>
<span data-ttu-id="3114a-103">A `Resume` příkaz zobrazovaly mimo kód pro zpracování chyb, nebo kód vstupovat do obslužná rutina chyby, i když se žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="3114a-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3114a-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3114a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="3114a-105">Přesunout `Resume` příkaz do obslužná rutina chyby, nebo ho odstranit.</span><span class="sxs-lookup"><span data-stu-id="3114a-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="3114a-106">Přechody na návěští nemůže nastat napříč postupy, proto vyhledejte postup pro popisek, který identifikuje obslužná rutina chyb.</span><span class="sxs-lookup"><span data-stu-id="3114a-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="3114a-107">Pokud zjistíte duplicitní popisek zadat jako cíl `GoTo` příkaz, který není `On Error GoTo` příkazu, Změna popisku řádku souhlas s jeho zamýšlenou cílovou.</span><span class="sxs-lookup"><span data-stu-id="3114a-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3114a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3114a-108">See also</span></span>

- [<span data-ttu-id="3114a-109">Příkaz Resume</span><span class="sxs-lookup"><span data-stu-id="3114a-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="3114a-110">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="3114a-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
