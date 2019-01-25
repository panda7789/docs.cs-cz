---
title: Obnovení práce bez chyby
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 55295997e5e534b091063815d5ad1a37b81638ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686618"
---
# <a name="resume-without-error"></a>Obnovení práce bez chyby
A `Resume` příkaz zobrazovaly mimo kód pro zpracování chyb, nebo kód vstupovat do obslužná rutina chyby, i když se žádná chyba.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přesunout `Resume` příkaz do obslužná rutina chyby, nebo ho odstranit.  
  
2.  Přechody na návěští nemůže nastat napříč postupy, proto vyhledejte postup pro popisek, který identifikuje obslužná rutina chyb. Pokud zjistíte duplicitní popisek zadat jako cíl `GoTo` příkaz, který není `On Error GoTo` příkazu, Změna popisku řádku souhlas s jeho zamýšlenou cílovou.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
