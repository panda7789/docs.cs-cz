---
title: Select – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 55c1e79b9e8e26483c1b7374a755bf977129169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604403"
---
# <a name="select-clause-visual-basic"></a>Select – klauzule (Visual Basic)
Definuje výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `var1`  
 Volitelné. Alias, který slouží k odkazování výsledky sloupcového výrazu.  
  
 `fieldName1`  
 Požadováno. Název pole, které chcete vrátit ve výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Select` klauzule k definování výsledků vrácených z dotazu. Díky tomu můžete buď zadat členy nové anonymní typ, který je vytvořen pomocí dotazu nebo pro cílové členy s názvem typu, který je vrácených dotazem. `Select` Klauzule není nutné pro dotaz. Pokud žádné `Select` je zadána klauzule, dotaz vrátí typ založený na všechny členy proměnných rozsahu identifikovat v aktuálním oboru. Další informace najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Když dotaz vytváří pojmenovaného typu, vrátí výsledek typu <xref:System.Collections.Generic.IEnumerable%601> kde `T` je typ vytvořený.  
  
 `Select` Klauzule odkazovat všechny proměnné v aktuálním oboru. To zahrnuje určené v proměnné rozsahu `From` – klauzule (nebo `From` klauzule). Zahrnuje také všechny nové proměnné, vytvořené pomocí alias pomocí `Aggregate`, `Let`, `Group By`, nebo `Group Join` klauzule nebo proměnné z předchozí `Select` klauzule ve výrazu dotazu. `Select` Klauzule může také obsahovat statické hodnoty. Například následující příklad kódu ukazuje výrazu dotazu, ve kterém `Select` klauzule definuje výsledek dotazu jako nový anonymní typ s čtyři členy: `ProductName`, `Price`, `Discount`, a `DiscountedPrice`. `ProductName` a `Price` z proměnnou rozsahu produktu, který je definován v člen hodnot, která `From` klauzule. `DiscountedPrice` Člen hodnota je vypočítána v `Let` klauzule. `Discount` Člen je statické hodnoty.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select` Klauzule zavádí novou sadu proměnných rozsahu pro klauzule následné dotazu a předchozí proměnné rozsahu již nejsou v oboru. Poslední `Select` klauzule ve výrazu dotazu určuje návratová hodnota dotazu. Například následující dotaz vrátí společnosti název a pořadí ID pro každý zákazníka pořadí, pro který překračuje celkové 500. První `Select` identifikuje proměnné rozsahu pro klauzuli `Where` klauzule a druhý `Select` klauzule. Druhý `Select` klauzule identifikuje hodnot vrácených dotazem jako nový typ anonymní.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Pokud `Select` klauzule identifikuje jednu položku vrátit, výrazu dotazu vrátí kolekci typ tohoto jednu položku. Pokud `Select` klauzule identifikuje více položek k vrácení, výrazu dotazu vrátí kolekci nový anonymní typ, a to podle vybrané položky. Například následující dva dotazy vrátí kolekce dva různé typy na základě `Select` klauzule. První dotaz vrátí kolekci názvů společnosti jako řetězce. Druhý dotaz vrátí kolekci `Customer` objekty naplněný názvy společnosti a informace o adrese.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro `customers` kolekce. `Select` Klauzule vybere jméno zákazníka a hodnota ID a naplní `CompanyName` a `CustomerID` sloupce novou proměnnou rozsahu. `For Each` Příkaz cyklicky prochází přes každý vrácený objekt a zobrazí se `CompanyName` a `CustomerID` sloupců pro každý záznam.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
