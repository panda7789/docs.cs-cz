---
title: "Nelze načíst pole, protože dvojité uvozovky není platný oddělovač EscapeQuotes nastavena na hodnotu True"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b5ee30da2146d6fa9841a80cc0e841bd737961f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nelze načíst pole, protože dvojité uvozovky není platný oddělovač EscapeQuotes nastavena na hodnotu True
`TextFieldParser` Nelze číst ze souboru, protože jako oddělovač, který má zadaný znak uvozovek (") a `EscapeQuotes` je nastaven na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nastavit `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také  
 [TextFieldParser.SetDelimiters Method](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters Property](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
