---
title: Pole s oddělovači nelze číst, protože dvojitá uvozovka není právní oddělovač, pokud je vlastnost EscapeQuotes nastavena na hodnotu true.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: cd2dd4226296ecd210a1e72a7b7fb593874b0008
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398471"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Pole s oddělovači nelze číst, protože dvojitá uvozovka není právní oddělovač, pokud je vlastnost EscapeQuotes nastavena na hodnotu true.
`TextFieldParser`Nelze číst ze souboru, protože znak uvozovky (") byl zadán jako oddělovač a `EscapeQuotes` je nastaven na hodnotu `True` .  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nastavte `EscapeQuotes` na `False` .  
  
## <a name="see-also"></a>Viz také

- [TextFieldParser. SetDelimiters – metoda](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser. oddělovače – vlastnost](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser – objekt](../language-reference/objects/textfieldparser-object.md)
