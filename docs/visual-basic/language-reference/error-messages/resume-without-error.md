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
# <a name="resume-without-error"></a>Obnovení práce bez chyby
A `Resume` příkaz zobrazovaly mimo kód pro zpracování chyb, nebo kód vstupovat do obslužná rutina chyby, i když se žádná chyba.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přesunout `Resume` příkaz do obslužná rutina chyby, nebo ho odstranit.  
  
2. Přechody na návěští nemůže nastat napříč postupy, proto vyhledejte postup pro popisek, který identifikuje obslužná rutina chyb. Pokud zjistíte duplicitní popisek zadat jako cíl `GoTo` příkaz, který není `On Error GoTo` příkazu, Změna popisku řádku souhlas s jeho zamýšlenou cílovou.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
