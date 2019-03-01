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
ms.openlocfilehash: 591fa664c56383cf8a7b3492e524a9738e065f8a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979603"
---
# <a name="select-clause-visual-basic"></a>Select – klauzule (Visual Basic)
Definuje výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `var1`  
 Volitelné. Alias, který slouží k odkazování výsledky výrazu sloupce.  
  
 `fieldName1`  
 Povinný parametr. Název pole má vrátit ve výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Select` klauzule k definování výsledků k vrácení z dotazu. To umožňuje definovat členy nové anonymní typ, který je vytvořen pomocí dotazu nebo cílové členy pojmenovaného typu, která je vrácena dotazem. `Select` Klauzule není vyžadován pro dotaz. Pokud ne `Select` není zadána klauzule, dotaz vrátí typ podle členů proměnných rozsahu, který je identifikován aktuálního oboru. Další informace najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Když dotaz slouží k vytvoření pojmenovaného typu, vrátí výsledek typu <xref:System.Collections.Generic.IEnumerable%601> kde `T` je typ vytvořený.  
  
 `Select` Klauzule můžete odkazovat na žádné proměnné v aktuálním oboru. To zahrnuje proměnné rozsahu podle `From` – klauzule (nebo `From` klauzule). Zahrnuje také všechny nové proměnné vytvořené pomocí alias podle `Aggregate`, `Let`, `Group By`, nebo `Group Join` klauzule nebo proměnné z předchozí `Select` klauzule ve výrazu dotazu. `Select` Klauzule může také obsahovat statické hodnoty. Například následující příklad kódu ukazuje výraz dotazu, ve kterém `Select` klauzule definuje výsledek dotazu jako nový anonymní typ s čtyři členy: `ProductName`, `Price`, `Discount`, a `DiscountedPrice`. `ProductName` a `Price` člen hodnoty pocházejí z proměnné rozsahu produktu, který je definován v `From` klauzuli. `DiscountedPrice` Hodnotu člen se počítá v `Let` klauzuli. `Discount` Člen je statický hodnotu.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select` Klauzule zavádí novou sadu proměnných rozsahu pro následné dotazování klauzule a předchozích proměnných rozsahu již nejsou v oboru. Poslední `Select` návratová hodnota dotazu určuje klauzuli ve výrazu dotazu. Například následující dotaz vrátí společnosti název a pořadí ID pro každý objednávku zákazníka, pro kterou celkový počet překročí 500. První `Select` identifikuje proměnné rozsahu pro klauzuli `Where` klauzule a druhá `Select` klauzuli. Druhá `Select` klauzule určuje hodnoty vrácené dotazem jako nové anonymního typu.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Pokud `Select` klauzule určuje jednu položku k vrácení, výrazu dotazu vrátí kolekci typu tuto jednu položku. Pokud `Select` klauzule určuje více položek k vrácení, výrazu dotazu vrátí kolekci nový anonymní typ, na základě vybraných položek. Například následující dva dotazy vrací kolekce na základě dvou různých typů `Select` klauzuli. První dotaz vrací kolekci názvů společnosti jako řetězce. Druhý dotaz vrátí kolekci `Customer` objekty vyplní názvy společností a informace o adrese.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro `customers` kolekce. `Select` Klauzule vybere jméno zákazníka a ID hodnotu a naplní `CompanyName` a `CustomerID` sloupce nové proměnné rozsahu. `For Each` Příkaz cyklickému každý vráceného objektu a zobrazí `CompanyName` a `CustomerID` sloupcích pro každý záznam.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Viz také:
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
