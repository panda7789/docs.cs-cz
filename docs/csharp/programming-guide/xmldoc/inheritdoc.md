---
title: Průvodce C# programováním <inheritdoc>
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795159"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc > (C# Průvodce programováním)

## <a name="syntax"></a>Syntaxe  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a>InheritDoc

Zdědit komentáře XML ze základních tříd, rozhraní a podobných metod. Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky se synchronizují komentáře XML. 
  
## <a name="remarks"></a>Poznámky  
Přidejte komentáře XML do základních tříd nebo rozhraní a umožněte InheritDoc kopírovat komentáře do implementací tříd.

Přidejte své komentáře XML do synchronních metod a umožněte InheritDoc kopírovat komentáře do asynchronních verzí stejných metod.  

Pokud chcete kopírovat komentáře z konkrétního člena, můžete použít atribut `cref` k určení člena.
  
## <a name="examples"></a>Příklady
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
