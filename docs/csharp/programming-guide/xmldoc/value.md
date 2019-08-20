---
title: <value> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 4d967d671b3a27698b457c80ff5a8f7031dc6bcb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587420"
---
# <a name="value-c-programming-guide"></a>\<Hodnota > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Popis vlastnosti  
  
## <a name="remarks"></a>Poznámky  
 \<Hodnota > tag umožňuje popsat hodnotu, kterou vlastnost představuje. Všimněte si, že při přidání vlastnosti prostřednictvím průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána [ \<souhrnná >](./summary.md) značka pro novou vlastnost. Měli byste pak ručně přidat \<hodnotu > značku k popisu hodnoty, kterou vlastnost představuje.  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
