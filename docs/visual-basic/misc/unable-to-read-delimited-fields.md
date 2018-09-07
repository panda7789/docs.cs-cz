---
title: Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: a119bf2592982b87c4bd361f9d125e6e8b7173c1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087222"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
`TextFieldParser` Nelze číst ze souboru, protože byl zadán jako oddělovač znak uvozovek (") a `EscapeQuotes` je nastavena na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nastavte `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také:

- [TextFieldParser.SetDelimiters – metoda](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)  
- [TextFieldParser.Delimiters Property](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)  
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
- [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
