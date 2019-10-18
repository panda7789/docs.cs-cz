---
title: <typeparam> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: e5e0d7be46e02bd30799b54246db729ae63ca300
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523284"
---
# <a name="typeparam-c-programming-guide"></a>> \<typeparam (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Název uzavřete do uvozovek ("").  
  
 `description`  
 Popis parametru typu.  
  
## <a name="remarks"></a>Poznámky  
 Značka `<typeparam>` by měla být použita v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu. Přidejte značku pro každý parametr typu obecného typu nebo metody.  
  
 Další informace najdete v tématu [Obecné typy](../generics/index.md).  
  
 Text značky `<typeparam>` bude zobrazen v IntelliSense, Webová sestava komentáře kódu [Prohlížeč objektů Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
