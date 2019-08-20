---
title: <param> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: e2e9bd4478ceaf2f491aba0aa3db8bae7857f28d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587920"
---
# <a name="param-c-programming-guide"></a>\<param >C# (Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Název uzavřete do uvozovek ("").  
  
 `description`  
 Popis parametru  
  
## <a name="remarks"></a>Poznámky  
 Značka \<> param by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu. Chcete-li zdokumentovat více parametrů \<, použijte více značek > param.  
  
 Text pro \<značku param > bude zobrazen v IntelliSense, v prohlížeč objektů a ve webové sestavě komentáře kódu.  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
