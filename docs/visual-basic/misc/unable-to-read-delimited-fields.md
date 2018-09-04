---
title: Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: faa42c2fec5851857496b321dbdb53c16c43e8c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525934"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
`TextFieldParser` Nelze číst ze souboru, protože byl zadán jako oddělovač znak uvozovek (") a `EscapeQuotes` je nastavena na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nastavte `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také  
 [TextFieldParser.SetDelimiters – metoda](https://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters Property](https://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
