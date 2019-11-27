---
title: Select – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 5ebb813229d5d517b369036c69b2d23c8ee1c9f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350412"
---
# <a name="select-clause-visual-basic"></a>Select – klauzule (Visual Basic)
Definuje výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `var1`  
 Volitelná. Alias, který lze použít k odkazování na výsledky výrazu sloupce.  
  
 `fieldName1`  
 Požadováno. Název pole, které se má vrátit do výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Klauzuli `Select` můžete použít k definování výsledků, které se mají vrátit z dotazu. To vám umožňuje definovat členy nového anonymního typu, který je vytvořen dotazem, nebo pro cílení členů pojmenovaného typu, který je vrácen dotazem. Klauzule `Select` není pro dotaz vyžadována. Pokud není zadána žádná klauzule `Select`, dotaz vrátí typ založený na všech členech proměnných rozsahu určených pro aktuální obor. Další informace najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Když dotaz vytvoří pojmenovaný typ, vrátí výsledek typu <xref:System.Collections.Generic.IEnumerable%601>, kde `T` je vytvořený typ.  
  
 Klauzule `Select` se může odkazovat na jakékoli proměnné v aktuálním oboru. To zahrnuje proměnné rozsahu identifikované v klauzuli `From` (nebo klauzule `From`). Obsahuje také všechny nové proměnné, které jsou vytvořeny s aliasem pomocí klauzulí `Aggregate`, `Let`, `Group By`nebo `Group Join`, nebo proměnných z předchozí klauzule `Select` ve výrazu dotazu. Klauzule `Select` může také zahrnovat statické hodnoty. Například následující příklad kódu ukazuje výraz dotazu, ve kterém klauzule `Select` definuje výsledek dotazu jako nový anonymní typ se čtyřmi členy: `ProductName`, `Price`, `Discount`a `DiscountedPrice`. Hodnoty členů `ProductName` a `Price` jsou pořízeny z proměnné rozsahu produktu, která je definována v klauzuli `From`. Hodnota člena `DiscountedPrice` je vypočítána v klauzuli `Let`. Člen `Discount` je statická hodnota.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 Klauzule `Select` zavádí novou sadu proměnných rozsahu pro následné klauzule dotazu a předchozí proměnné rozsahu již nejsou v oboru. Poslední klauzule `Select` ve výrazu dotazu určuje návratovou hodnotu dotazu. Například následující dotaz vrátí název společnosti a ID objednávky pro každé pořadí zákazníků, pro které součet převyšuje 500. Klauzule First `Select` identifikuje proměnné rozsahu pro klauzuli `Where` a druhou klauzuli `Select`. Druhá klauzule `Select` identifikuje hodnoty vrácené dotazem jako nový anonymní typ.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Pokud klauzule `Select` identifikuje jednu položku, která se má vrátit, výraz dotazu vrátí kolekci typu dané jedné položky. Pokud klauzule `Select` identifikuje více položek, které mají být vráceny, výraz dotazu vrátí kolekci nového anonymního typu na základě vybraných položek. Například následující dva dotazy vrátí kolekce dvou různých typů na základě klauzule `Select`. První dotaz vrátí kolekci názvů společností jako řetězce. Druhý dotaz vrátí kolekci `Customer` objektů vyplněných názvy společnosti a informacemi o adrese.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro kolekci `customers`. Klauzule `Select` vybírá název a hodnotu ID zákazníka a naplní sloupce `CompanyName` a `CustomerID` nové proměnné rozsahu. Příkaz `For Each` projde každým vráceným objektem a zobrazí `CompanyName` a `CustomerID` sloupců pro každý záznam.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
