---
title: Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: ca764d5258daf54a7149661549a78b3aca709718
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619806"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nelze číst pole oddělená oddělovačem, protože dvojité uvozovky nepředstavují platný oddělovač při EscapeQuotes nastavena na hodnotu True
`TextFieldParser` Nelze číst ze souboru, protože byl zadán jako oddělovač znak uvozovek (") a `EscapeQuotes` je nastavena na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nastavte `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také:

- [TextFieldParser.SetDelimiters Method](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser.Delimiters Property](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
