---
title: "Nelze načíst pole, protože dvojité uvozovky není platný oddělovač EscapeQuotes nastavena na hodnotu True"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3644165d0c25189f29f3f878a17b0d9bf4e2623b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nelze načíst pole, protože dvojité uvozovky není platný oddělovač EscapeQuotes nastavena na hodnotu True
`TextFieldParser` Nelze číst ze souboru, protože jako oddělovač, který má zadaný znak uvozovek (") a `EscapeQuotes` je nastaven na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nastavit `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také  
 [TextFieldParser.SetDelimiters – metoda](http://msdn.microsoft.com/en-us/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [Vlastnost TextFieldParser.Delimiters](http://msdn.microsoft.com/en-us/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Postupy: čtení z oddělených čárkou textových souborů](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser – objekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
