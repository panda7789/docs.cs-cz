---
title: '&lt;Param&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338010"
---
# <a name="ltparamgt-c-programming-guide"></a>&lt;Param&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Uzavřete název do dvojitých uvozovek nahoře ("").  
  
 `description`  
 Popis parametru.  
  
## <a name="remarks"></a>Poznámky  
 \<Param > Značka je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu. K dokumentu několik parametrů, použijte více \<param > značky.  
  
 Text pro \<param > Značka se zobrazí v technologii IntelliSense, prohlížeč objektů a sestava webové komentář kódu.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
