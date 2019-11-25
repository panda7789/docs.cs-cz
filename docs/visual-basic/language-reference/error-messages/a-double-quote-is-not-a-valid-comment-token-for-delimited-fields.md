---
title: Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976219"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.

Jako oddělovač `TextFieldParser`byl dodán znak uvozovky, ale `EscapeQuotes` je nastaven na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nastavte `EscapeQuotes` na `False`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
