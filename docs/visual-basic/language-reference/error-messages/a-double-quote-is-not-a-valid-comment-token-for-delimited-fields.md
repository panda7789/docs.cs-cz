---
title: Dvojité uvozovky nepředstavují platný token komentáře pro pole oddělené oddělovačem, kde parametr EscapeQuote je nastaven na hodnotu True.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 809cb2ab6e84f8c7f14f5a3b03dfc6142a31b5bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558966"
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
