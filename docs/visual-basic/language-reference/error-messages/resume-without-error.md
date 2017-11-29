---
title: "Obnovení práce bez chyby"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="e9a05-102">Obnovení práce bez chyby</span><span class="sxs-lookup"><span data-stu-id="e9a05-102">Resume without error</span></span>
<span data-ttu-id="e9a05-103">A `Resume` příkaz zobrazovaly mimo kód pro ošetření chyb nebo kód přešli do obslužnou rutinu chyby i v případě, že se žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="e9a05-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9a05-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e9a05-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="e9a05-105">Přesunout `Resume` příkaz do obslužnou rutinu chyby, nebo ho odstranit.</span><span class="sxs-lookup"><span data-stu-id="e9a05-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="e9a05-106">Přeskočí popisky nemůže proběhnout mezi postupy, takže vyhledávání postup pro štítek, který identifikuje obslužná rutina chyb.</span><span class="sxs-lookup"><span data-stu-id="e9a05-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="e9a05-107">Pokud se vám najít duplicitní štítek zadaný jako cíl `GoTo` příkaz, který není `On Error GoTo` příkaz, změňte popisek čáry potvrdíte svůj souhlas s jeho zamýšleného cílového.</span><span class="sxs-lookup"><span data-stu-id="e9a05-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a05-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a05-108">See Also</span></span>  
 [<span data-ttu-id="e9a05-109">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9a05-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="e9a05-110">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9a05-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
