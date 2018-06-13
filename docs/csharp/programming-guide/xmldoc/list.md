---
title: '&lt;seznam&gt; (C# Průvodce programováním)'
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
ms.openlocfilehash: 768490424403f1235873a681ffba3367e3f128b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337727"
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;seznam&gt; (C# Průvodce programováním)
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
 Termín, definovat, které budou určené v `description`.  
  
 `description`  
 Buď položku v odrážku nebo číslovaný seznam nebo definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 \<Listheader > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí zadat položku termín v záhlaví.  
  
 Každá položka v seznamu je definován s \<položky > bloku. Při vytváření definice seznamu, budete muset zadat oba seznamy `term` a `description`. Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít jako mnoho \<položky > blokuje podle potřeby.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
