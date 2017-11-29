---
title: "Order By – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ee21942b966668a67b14aba72b8f9fc5ee903c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-clause-visual-basic"></a>Order By – klauzule (Visual Basic)
Určuje pořadí řazení výsledků dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `orderExp1`  
 Požadováno. Minimálně jedno pole z aktuální výsledek dotazu, které zjišťují, jak pořadí vrácených hodnot. Názvy polí musí být oddělené čárkami (,). Každé pole můžete identifikovat jako seřazený ve vzestupném nebo sestupném pořadí pomocí `Ascending` nebo `Descending` klíčová slova. Pokud žádné `Ascending` nebo `Descending` je zadané klíčové slovo, je vzestupné výchozí pořadí řazení. Pole pořadí řazení mají přednost před zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Order By` klauzule k řazení výsledků dotazu. `Order By` Klauzule může seřadit pouze výsledku založené na proměnnou rozsahu pro aktuální obor. Například `Select` klauzule zavádí nový obor ve výrazu dotazu s nové proměnné iterace pro tento obor. Proměnné definované před v rozsahu `Select` klauzuli v dotazu nejsou k dispozici po `Select` klauzule. Proto pokud chcete výsledky podle pole, která není k dispozici v pořadí `Select` klauzule, musíte umístit `Order By` klauzule před `Select` klauzule. Jedna je například pokud bude potřeba to udělat v případě, že chcete seřadit podle pole, které nejsou v rámci výsledku dotazu.  
  
 Vzestupné a sestupném pořadí pro pole je dáno implementace <xref:System.IComparable> rozhraní pro datový typ pole. Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení je ignorována.  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `book` pro `books` kolekce. `Order By` Klauzule seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí). Knih za stejnou cenu. jsou seřazené podle názvu ve vzestupném pořadí. `Select` Klauzule vybere `Title` a `Price` vlastnosti jako hodnoty vrácených dotazem.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `Order By` klauzule výsledek dotazu seřadit cenu v sestupném pořadí. Knih za stejnou cenu. jsou seřazené podle názvu ve vzestupném pořadí.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `Select` klauzule vyberte název adresáře, cena, publikovat data a vytvářet. Pak naplní `Title`, `Price`, `PublishDate`, a `Author` pole proměnnou rozsahu nového oboru. `Order By` Klauzule řadí nové proměnné rozsahu jméno autora, název knihy a ceny. Každý sloupec je seřazen v pořadí (vzestupně).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)
