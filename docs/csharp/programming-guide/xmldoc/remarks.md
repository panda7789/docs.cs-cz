---
title: <remarks> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975846"
---
# <a name="remarks-c-programming-guide"></a>\<REMARKS > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Description`  
 Popis člena.  
  
## <a name="remarks"></a>Poznámky  
 \<Remarks > Značka se používá k přidání informací o typu, doplňující informace zadaným [ \<summary >](../../../csharp/programming-guide/xmldoc/summary.md). Tyto informace se zobrazí v okně prohlížeče objektů.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
