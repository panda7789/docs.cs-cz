---
title: <typeparamref> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a9b0b9dec09e891105336b3cf0088ed279386d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706569"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Název uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Další informace o parametrech typu v obecné typy a metody, naleznete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).  
  
 Použijte tuto značku k povolení příjemcům soubor dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
