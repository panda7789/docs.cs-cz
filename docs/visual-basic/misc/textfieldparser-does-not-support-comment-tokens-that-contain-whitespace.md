---
title: TextFieldParser nepodporuje tokeny komentářů obsahující prázdné znaky.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 51dc2b82d7f04c652e18173b8450b65c15ee6ec2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411893"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nepodporuje tokeny komentářů obsahující prázdné znaky.
Byl zadán token komentáře obsahující prázdné znaky. Nepodporuje `TextFieldParser` tokeny komentáře obsahující prázdné znaky, pokud prázdné místo nevzniká na začátku tokenu. Prázdné znaky, ke kterým dochází na začátku tokenu, se ignorují.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zadejte správný token komentáře.  
  
## <a name="see-also"></a>Viz také

- [TextFieldParser. CommentTokens – vlastnost](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [Analýza textových souborů pomocí objektu TextFieldParser](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [TextFieldParser – objekt](../language-reference/objects/textfieldparser-object.md)
