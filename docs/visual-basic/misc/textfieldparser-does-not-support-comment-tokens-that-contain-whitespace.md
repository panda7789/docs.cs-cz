---
title: TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: a8931d67cd728cf98bc4d83044c65fad6642b021
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252802"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
Byl zadán token komentář, který obsahuje prázdné znaky. `TextFieldParser` Nepodporuje tokeny komentáře obsahující prázdné znaky, pokud prázdné místo nastane na začátku token. Prázdné znaky, ke kterým dochází na začátku token se ignoruje.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte správný komentáři tokenu.  
  
## <a name="see-also"></a>Viz také:

- [TextFieldParser.CommentTokens Property](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)  
- [Analýza textových souborů pomocí objektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
- [Objekt TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
