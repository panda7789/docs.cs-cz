---
title: <value> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: a30435c40ad31e026b9cb1952086984548f0cdb6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694540"
---
# <a name="value-c-programming-guide"></a>> hodnota \<(C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Popis vlastnosti  
  
## <a name="remarks"></a>Poznámky  
 Hodnota \<> tag umožňuje popsat hodnotu, kterou vlastnost představuje. Všimněte si, že při přidání vlastnosti přes průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána značka [\<summary >](./summary.md) pro novou vlastnost. Měli byste pak ručně přidat \<Value > tag k popisu hodnoty, kterou vlastnost představuje.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
