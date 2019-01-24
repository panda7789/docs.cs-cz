---
title: TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 9a14bc29ecfa917b6213f32cd170aa83d6f60f58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525011"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
Byl zadán token komentář, který obsahuje prázdné znaky. `TextFieldParser` Nepodporuje tokeny komentáře obsahující prázdné znaky, pokud prázdné místo nastane na začátku token. Prázdné znaky, ke kterým dochází na začátku token se ignoruje.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte správný komentáři tokenu.  
  
## <a name="see-also"></a>Viz také:

- [TextFieldParser.CommentTokens Property](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
