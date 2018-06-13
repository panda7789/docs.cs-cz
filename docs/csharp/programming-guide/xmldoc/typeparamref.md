---
title: '&lt;typeparamref&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 36e5a8998018839214da00287a2bf8dc2c5925a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356260"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a>&lt;typeparamref&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Uzavřete název do dvojitých uvozovek nahoře ("").  
  
## <a name="remarks"></a>Poznámky  
 Další informace o parametrech typu v obecné typy a metody najdete v tématu [obecné typy](../../../csharp/programming-guide/generics/index.md).  
  
 Použijte tuto značku k povolení příjemcům souboru dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
