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
---
# <a name="resume-without-error"></a>Obnovení práce bez chyby
A `Resume` příkaz zobrazovaly mimo kód pro ošetření chyb nebo kód přešli do obslužnou rutinu chyby i v případě, že se žádná chyba.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přesunout `Resume` příkaz do obslužnou rutinu chyby, nebo ho odstranit.  
  
2.  Přeskočí popisky nemůže proběhnout mezi postupy, takže vyhledávání postup pro štítek, který identifikuje obslužná rutina chyb. Pokud se vám najít duplicitní štítek zadaný jako cíl `GoTo` příkaz, který není `On Error GoTo` příkaz, změňte popisek čáry potvrdíte svůj souhlas s jeho zamýšleného cílového.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
