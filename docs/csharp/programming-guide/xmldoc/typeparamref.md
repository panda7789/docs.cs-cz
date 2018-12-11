---
title: '&lt;typeparamref&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: bbe9bed5a32e463424b98f4066e95374401931e2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243917"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a>&lt;typeparamref&gt; (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Název uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Další informace o parametrech typu v obecné typy a metody, naleznete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).  
  
 Použijte tuto značku k povolení příjemcům soubor dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
