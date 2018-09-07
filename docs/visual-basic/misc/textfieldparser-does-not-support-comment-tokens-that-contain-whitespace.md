---
title: TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 2beda651dba952969593ffc7d64f01fd51ab7919
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070885"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
Byl zadán token komentář, který obsahuje prázdné znaky. `TextFieldParser` Nepodporuje tokeny komentáře obsahující prázdné znaky, pokud prázdné místo nastane na začátku token. Prázdné znaky, ke kterým dochází na začátku token se ignoruje.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte správný komentáři tokenu.  
  
## <a name="see-also"></a>Viz také  
 [TextFieldParser.CommentTokens Property](https://msdn.microsoft.com/library/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)  
 [Analýza textových souborů pomocí objektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
