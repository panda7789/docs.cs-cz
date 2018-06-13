---
title: Obnovení práce bez chyby
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597872"
---
# <a name="resume-without-error"></a><span data-ttu-id="38b20-102">Obnovení práce bez chyby</span><span class="sxs-lookup"><span data-stu-id="38b20-102">Resume without error</span></span>
<span data-ttu-id="38b20-103">A `Resume` příkaz zobrazovaly mimo kód pro ošetření chyb nebo kód přešli do obslužnou rutinu chyby i v případě, že se žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="38b20-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38b20-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="38b20-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="38b20-105">Přesunout `Resume` příkaz do obslužnou rutinu chyby, nebo ho odstranit.</span><span class="sxs-lookup"><span data-stu-id="38b20-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="38b20-106">Přeskočí popisky nemůže proběhnout mezi postupy, takže vyhledávání postup pro štítek, který identifikuje obslužná rutina chyb.</span><span class="sxs-lookup"><span data-stu-id="38b20-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="38b20-107">Pokud se vám najít duplicitní štítek zadaný jako cíl `GoTo` příkaz, který není `On Error GoTo` příkaz, změňte popisek čáry potvrdíte svůj souhlas s jeho zamýšleného cílového.</span><span class="sxs-lookup"><span data-stu-id="38b20-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b20-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="38b20-108">See Also</span></span>  
 [<span data-ttu-id="38b20-109">Příkaz Resume</span><span class="sxs-lookup"><span data-stu-id="38b20-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="38b20-110">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="38b20-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
