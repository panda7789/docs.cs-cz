---
title: Průvodce C# programováním <exception>
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 4e4204996c006ce6e943c9a09661001b0e0c2a14
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523470"
---
# <a name="exception-c-programming-guide"></a>> \<exception (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML. `member` musí být v uvozovkách ("").  
  
 Další informace o tom, jak formátovat `member` pro odkazování na obecný typ, naleznete v tématu [zpracování souboru XML](processing-the-xml-file.md).
  
 `description`  
 Popis výjimky  
  
## <a name="remarks"></a>Poznámky  
 Značka > \<exception umožňuje určit, které výjimky mohou být vyvolány. Tato značka se dá použít na definice pro metody, vlastnosti, události a indexery.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
 Další informace o zpracování výjimek naleznete v tématu [výjimky a zpracování výjimek](../exceptions/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](recommended-tags-for-documentation-comments.md)
