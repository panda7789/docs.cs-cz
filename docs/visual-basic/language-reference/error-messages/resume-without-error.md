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
# <a name="resume-without-error"></a>Obnovení práce bez chyby
`Resume`Příkaz se objevil mimo kód pro zpracování chyb, nebo se kód přeskočí do obslužné rutiny chyb, i když došlo k chybě.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přesuňte `Resume` příkaz do obslužné rutiny chyb nebo jej odstraňte.  
  
2. K popiskům nelze v rámci procedur vyskytovat, proto v proceduře vyhledejte popisek, který identifikuje obslužnou rutinu chyby. Pokud najdete duplicitní popisek zadaný jako cíl `GoTo` příkazu, který není `On Error GoTo` příkazem, změňte popisek řádku tak, aby souhlasil s jeho zamýšleným cílem.  
  
## <a name="see-also"></a>Viz také

- [Resume – příkaz](../statements/resume-statement.md)
- [On Error – příkaz](../statements/on-error-statement.md)
