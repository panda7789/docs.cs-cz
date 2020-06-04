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
ms.openlocfilehash: a909b1d79b10f82ece03bab788ae889c64b27124
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359691"
---
# <a name="select-clause-visual-basic"></a>Select – klauzule (Visual Basic)
Definuje výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `var1`  
 Nepovinný parametr. Alias, který lze použít k odkazování na výsledky výrazu sloupce.  
  
 `fieldName1`  
 Povinná hodnota. Název pole, které se má vrátit do výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Klauzuli můžete použít `Select` k definování výsledků, které se mají vrátit z dotazu. To vám umožňuje definovat členy nového anonymního typu, který je vytvořen dotazem, nebo pro cílení členů pojmenovaného typu, který je vrácen dotazem. `Select`Klauzule není pro dotaz vyžadována. Pokud `Select` není zadána žádná klauzule, dotaz vrátí typ založený na všech členech proměnných rozsahu určených pro aktuální obor. Další informace najdete v tématu [anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md). Když dotaz vytvoří pojmenovaný typ, vrátí výsledek typu, <xref:System.Collections.Generic.IEnumerable%601> kde `T` je vytvořený typ.  
  
 `Select`Klauzule může odkazovat na jakékoli proměnné v aktuálním oboru. To zahrnuje proměnné rozsahu identifikované v `From` klauzuli (nebo `From` klauzulí). Zahrnuje také všechny nové proměnné vytvořené s aliasem `Aggregate` , pomocí klauzulí, `Let` , `Group By` , nebo `Group Join` proměnných z předchozí `Select` klauzule ve výrazu dotazu. `Select`Klauzule může také zahrnovat statické hodnoty. Například následující příklad kódu ukazuje výraz dotazu, ve kterém `Select` klauzule definuje výsledek dotazu jako nový anonymní typ se čtyřmi členy: `ProductName` , `Price` , `Discount` a `DiscountedPrice` . `ProductName` `Price` Hodnoty členů a jsou získány z proměnné rozsahu produktu, která je definována v `From` klauzuli. `DiscountedPrice`Hodnota člena je vypočítána v `Let` klauzuli. `Discount`Člen je statická hodnota.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`Klauzule zavádí novou sadu proměnných rozsahu pro následné klauzule dotazu a předchozí proměnné rozsahu již nejsou v oboru. Poslední `Select` klauzule ve výrazu dotazu určuje návratovou hodnotu dotazu. Například následující dotaz vrátí název společnosti a ID objednávky pro každé pořadí zákazníků, pro které součet převyšuje 500. První `Select` klauzule identifikuje proměnné rozsahu pro `Where` klauzuli a druhou `Select` klauzuli. Druhá `Select` klauzule identifikuje hodnoty vrácené dotazem jako nový anonymní typ.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Pokud `Select` klauzule identifikuje jedinou položku, která se má vrátit, výraz dotazu vrátí kolekci typu dané jedné položky. Pokud `Select` klauzule identifikuje více položek, které mají být vráceny, výraz dotazu vrátí kolekci nového anonymního typu na základě vybraných položek. Například následující dva dotazy vrátí kolekce dvou různých typů na základě `Select` klauzule. První dotaz vrátí kolekci názvů společností jako řetězce. Druhý dotaz vrátí kolekci `Customer` objektů vyplněných názvy společnosti a informacemi o adrese.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `cust` pro `customers` kolekci. `Select`Klauzule vybere jméno zákazníka a hodnotu ID a naplní `CompanyName` `CustomerID` sloupce a nové proměnné rozsahu. `For Each`Příkazy projde každým vráceným objektem a zobrazí `CompanyName` `CustomerID` sloupce a pro každý záznam.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule WHERE](where-clause.md)
- [Order By – klauzule](order-by-clause.md)
- [Anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
