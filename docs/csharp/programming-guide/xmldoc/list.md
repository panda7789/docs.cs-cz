---
title: <list> – C# Průvodce programováním
ms.custom: seodec18
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
ms.openlocfilehash: aadb24c43d49acb3e71490efd156b14d9fc5f133
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587969"
---
# <a name="list-c-programming-guide"></a>\<seznam > (C# Průvodce programováním)
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
  
## <a name="parameters"></a>Parametry  
 `term`  
 Pojem, který definuje, který bude definován v `description`.  
  
 `description`  
 Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 Blok \<listheader – > slouží k definování řádku záhlaví v seznamu tabulek nebo definic. Při definování tabulky stačí zadat položku pro termín v záhlaví.  
  
 Každá položka v seznamu je určena pomocí \<> blok položky. Při vytváření seznamu definic budete muset zadat i `term`. `description` U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít podle potřeby tolik \<> bloků položek.  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
