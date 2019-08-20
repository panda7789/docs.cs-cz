---
title: <typeparamref>– C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: f01df27b920dcf3011a51015c771d2da3b442c4c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587427"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Název uzavřete do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Další informace o parametrech typu v obecných typech a metodách naleznete [](../generics/index.md)v tématu generické typy.  
  
 Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
