---
title: Literály s hodnotou null a odvození typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: bb2d9184e17ee2a9916a731eb20eefa105a73753
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249821"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Literály s hodnotou null a odvození typu (Entity SQL)
Literály null jsou kompatibilní s jakýmkoli typem v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systému typů. Nicméně pro typ literálu s hodnotou null, který má být odvozen správně, ukládá [!INCLUDE[esql](../../../../../../includes/esql-md.md)] určitá omezení, kde lze použít literál null.  
  
## <a name="typed-nulls"></a>Typové hodnoty null  
 Typové hodnoty null lze použít kdekoli. Odvození typu není vyžadováno pro zadané hodnoty null, protože je znám typ. Například můžete vytvořit hodnotu null typu Int16 s následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcí:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Volné literály s nulovým číslem  
 Volné literály s hodnotou null lze použít v následujících kontextech:  
  
- Jako argument pro výraz CAST nebo považovat. Toto je doporučený způsob vytvoření typovaného výrazu s hodnotou null.  
  
- Jako argument metody nebo funkce. Platí standardní pravidla přetížení.  
  
- Jako jeden z argumentů aritmetického výrazu, jako je například +,-nebo/. Ostatní argumenty nemohou být literály null, jinak odvození typu není možné.  
  
- Jako kterýkoli z argumentů logického výrazu (a, nebo). Všechny argumenty jsou známy jako typ Boolean.  
  
- , Protože argument má hodnotu NULL nebo není NULL výraz.  
  
- Jako jeden nebo více argumentů výrazu LIKE. Očekává se, že všechny argumenty budou řetězce.  
  
- Jako jeden nebo více argumentů konstruktoru pojmenovaného typu.  
  
- Jako jeden nebo více argumentů konstruktoru multiset. Nejméně jeden argument konstruktoru multiset musí být výraz, který není literál s hodnotou null.  
  
- Jako jeden nebo více výrazů THEN nebo ELSE ve výrazu CASE. Nejméně jeden z výrazů THEN nebo ELSE ve výrazu CASE musí být výrazem jiným než literál s hodnotou null.  
  
 V jiných scénářích nelze použít prázdné literály s nulovým číslem. Nelze je například použít jako argumenty konstruktoru řádku.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
