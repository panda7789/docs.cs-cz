---
title: Literály s hodnotou Null a odvození typu proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 22b548f2fc889b20f76a41001438f75c25f99c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118089"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Literály s hodnotou Null a odvození typu proměnné (Entity SQL)
Literály s hodnotou Null, musí být kompatibilní s žádným typem v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systém typů. Typu literál s hodnotou null odvození správně, ale pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] má určitá omezení pro použití literál s hodnotou null.  
  
## <a name="typed-nulls"></a>Zadané hodnoty Null  
 Zadané hodnoty Null lze použít kdekoli. Odvození typu proměnné není požadované pro zadané hodnoty Null, protože typ je znám. Například můžete vytvořit s hodnotou null typu Int16 následujícím [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvořit:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Plovoucí literály s hodnotou Null  
 Plovoucí literály s hodnotou null lze použít v následujících kontextů:  
  
-   Jako argument výraz PŘETYPOVÁNÍ nebo POVAŽOVAT. Toto je doporučený postup pro vytvoření zadaný nulový výraz.  
  
-   Jako argument metody nebo funkce. Platí standardní přetížení pravidla.  
  
-   Jako jeden z argumentů pro aritmetický výraz jako +, -, nebo /. Další argumenty nemůžou být literály s hodnotou null, jinak odvození typu proměnné není možné.  
  
-   Jako některý z argumentů na logický výraz (AND, OR, nebo ne). Všechny argumenty jsou známé jako typu Boolean.  
  
-   Jako argument výraz IS NULL a IS NOT NULL.  
  
-   Jako jeden nebo více argumentů STEJNÉHO výrazu. Všechny argumenty jsou má být řetězce.  
  
-   Jako jeden nebo více argumentů konstruktoru s názvem typu.  
  
-   Jako jeden nebo více argumentů pro konstruktor multiset. Alespoň jeden argument pro konstruktor multiset musí být výraz, který není literál s hodnotou null.  
  
-   Jako jeden nebo více výrazů ve výrazu případu potom nebo jinak. Nejméně jeden z výrazů v výraz CASE pak nebo jinak musí být výrazem jiným než literál s hodnotou null.  
  
 Plovoucí literály s hodnotou null nelze použít v jiných scénářích. Například nelze je použít jako argumenty pro konstruktor row.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
