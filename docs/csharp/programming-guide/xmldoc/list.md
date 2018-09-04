---
title: '&lt;seznam&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 3f9d1e2b08b672ca58e96767aedaa71a8826c0ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512429"
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;seznam&gt; (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametry  
 `term`  
 Termín, který chcete definovat, které budou určené v `description`.  
  
 `description`  
 Buď položku v odrážkami nebo číslovaný seznam nebo definici `term`.  
  
## <a name="remarks"></a>Poznámky  
 \<Listheader – > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí zadat položky pro výraz v záhlaví.  
  
 Každá položka v seznamu není zadán s \<položky > bloku. Při vytváření definice seznamu, budete muset zadat současně `term` a `description`. Ale pro tabulku, seznam s odrážkami nebo číslovaného seznamu, stačí zadat položku pro `description`.  
  
 Seznam nebo tabulku můžete mít kolik \<položky > blokuje podle potřeby.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
