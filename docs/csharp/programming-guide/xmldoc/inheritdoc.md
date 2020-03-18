---
title: <inheritdoc>- Průvodce programováním jazyka C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156945"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (Průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

Dědit xml komentáře ze základních tříd, rozhraní a podobné metody. Tím se eliminuje nechtěné kopírování a vkládání duplicitních komentářů XML a automaticky udržuje komentáře XML synchronizované.
  
## <a name="remarks"></a>Poznámky  
Přidejte komentáře XML do základních tříd nebo rozhraní a nechte InheritDoc zkopírovat komentáře do implementujících tříd.

Přidejte komentáře XML do synchronních metod a nechte InheritDoc zkopírovat komentáře do asynchronních verzí stejných metod.  

Pokud chcete zkopírovat komentáře z určitého člena, můžete použít `cref` atribut k určení člena.
  
## <a name="examples"></a>Příklady
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Doporučené značky pro komentáře k dokumentaci](./recommended-tags-for-documentation-comments.md)
