---
title: "Select – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d8cabcbd8554ca2aee639eaac8a52f0485a266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Order By – klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
