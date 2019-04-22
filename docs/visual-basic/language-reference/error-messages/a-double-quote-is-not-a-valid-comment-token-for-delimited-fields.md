---
title: Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 6e55fde395cec2fcd4053e66d855750945ea1448
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840858"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
Jako oddělovač pro byl uveden znak uvozovek `TextFieldParser`, ale `EscapeQuotes` je nastavena na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nastavte `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
