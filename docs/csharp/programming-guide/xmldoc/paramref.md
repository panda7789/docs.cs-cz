---
title: Průvodce C# programováním <paramref>
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 42c428b74f0df9d4ca37e85d805db8012670521c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696542"
---
# <a name="paramref-c-programming-guide"></a>\<paramref > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru, na který se má odkazovat Název uzavřete do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Značka > \<paramref poskytuje způsob, jak označit, že slovo v komentářích kódu, například v \<Summary > nebo \<poznámky > blok odkazuje na parametr. Soubor XML lze zpracovat pro formátování tohoto slova nějakým způsobem, například tučným písmem nebo kurzívou.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
