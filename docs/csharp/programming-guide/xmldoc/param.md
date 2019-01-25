---
title: '&lt;Param&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641015"
---
# <a name="ltparamgt-c-programming-guide"></a>&lt;Param&gt; (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Název uzavřete do dvojitých uvozovek ("").  
  
 `description`  
 Popis pro parametr.  
  
## <a name="remarks"></a>Poznámky  
 \<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu. Do dokumentu více parametrů, použijte více \<param > značky.  
  
 Text \<param > značky se zobrazí v IntelliSense, prohlížeči objektů a v sestavě webového kódu komentář.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
