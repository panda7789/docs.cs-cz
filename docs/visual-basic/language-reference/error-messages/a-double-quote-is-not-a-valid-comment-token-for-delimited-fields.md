---
title: Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: b49a3223c6638adff757d7d82aee549cb1fee473
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646929"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
Jako oddělovač pro byl uveden znak uvozovek `TextFieldParser`, ale `EscapeQuotes` je nastavena na `True`.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nastavte `EscapeQuotes` k `False`.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
