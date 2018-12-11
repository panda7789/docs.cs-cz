---
title: '&lt;paramref&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 90c22b81f17adb1fcfdb94f32047e85c0bd8f4e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243618"
---
# <a name="ltparamrefgt-c-programming-guide"></a>&lt;paramref&gt; (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru jako reference. Název uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Paramref > značky poskytuje způsob, jak určit, že slovo v kódu komentáře, například v \<summary > nebo \<Poznámky > bloku odkazuje na parametr. Soubor XML mohou být zpracovány do naformátuje toto slovo distinct způsobem, jako tučný nebo kurzívu písma.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
