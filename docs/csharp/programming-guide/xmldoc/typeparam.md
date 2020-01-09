---
title: <typeparam> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 04145b82cbed0e9a5cae38ff9ef33d061ee792c9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694527"
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
