---
title: "Obnovení práce bez chyby"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a>Obnovení práce bez chyby
A `Resume` příkaz zobrazovaly mimo kód pro ošetření chyb nebo kód přešli do obslužnou rutinu chyby i v případě, že se žádná chyba.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přesunout `Resume` příkaz do obslužnou rutinu chyby, nebo ho odstranit.  
  
2.  Přeskočí popisky nemůže proběhnout mezi postupy, takže vyhledávání postup pro štítek, který identifikuje obslužná rutina chyb. Pokud se vám najít duplicitní štítek zadaný jako cíl `GoTo` příkaz, který není `On Error GoTo` příkaz, změňte popisek čáry potvrdíte svůj souhlas s jeho zamýšleného cílového.  
  
## <a name="see-also"></a>Viz také  
 [Resume – příkaz](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error – příkaz](../../../visual-basic/language-reference/statements/on-error-statement.md)
