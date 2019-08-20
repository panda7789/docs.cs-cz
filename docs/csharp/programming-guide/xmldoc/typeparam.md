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
ms.openlocfilehash: ea48cf0cdfc2dc48ad29ab6219449f801739bc8f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587594"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Průvodce programováním)
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
 `<typeparam>` Značka by měla být použita v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu. Přidejte značku pro každý parametr typu obecného typu nebo metody.  
  
 Další informace najdete v tématu [Obecné typy](../generics/index.md).  
  
 Text `<typeparam>` značky bude zobrazen v IntelliSense, Webová sestava komentáře kódu [prohlížeč objektůho okna](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
