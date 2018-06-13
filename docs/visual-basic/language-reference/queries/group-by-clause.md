---
title: Group By – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 7cf688dc2e0ccd10c8bfbe5f0308f0aa808fbef0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605027"
---
# <a name="group-by-clause-visual-basic"></a>Group By – klauzule (Visual Basic)
Skupiny elementy výsledků dotazu. Můžete také použít k použití agregační funkce pro každou skupinu. Operace seskupení je založena na jeden nebo více klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Součásti  
  
-   `listField1`, `listField2`  
  
     Volitelné. Jeden nebo více polí proměnné dotazu nebo proměnné, které explicitně určit pole, která má být zahrnut v seskupené výsledek. Pokud nejsou zadaná žádná pole, všechna pole dotazu proměnné nebo proměnné jsou součástí seskupené výsledek.  
  
-   `keyExp1`  
  
     Požadováno. Výraz, který identifikuje klíč sloužící k určení skupiny elementů. Můžete zadat více než jeden klíč k určení složený klíč.  
  
-   `keyExp2`  
  
     Volitelné. Jeden nebo více dalších klíčů, které jsou spojené s `keyExp1` k vytvoření složeného klíče.  
  
-   `aggregateList`  
  
     Požadováno. Jeden nebo více výrazů, které určují, jak jsou agregovat do skupin. Lze zjistit název člena seskupené výsledků `Group` – klíčové slovo, které může být v některém z následujících podob:  
  
    ```  
    Into Group  
    ```  
  
     -nebo-  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Můžete použít také agregační funkce na aplikujete na skupinu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Group By` klauzule rozdělte výsledků dotazu do skupin. Seskupení podle klíče nebo složený klíč, který se skládá z více klíčů. Elementy, které jsou spojeny s odpovídajícím hodnoty klíče jsou součástí stejné skupiny.  
  
 Můžete použít `aggregateList` parametr `Into` klauzule a `Group` – klíčové slovo k identifikaci název člena, který slouží k odkazování skupině. Můžete použít také agregačních funkcí ve `Into` klauzule k výpočtu hodnoty pro seskupené elementy. Seznam standardní agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu skupiny seznamu odběratelů založené na jejich umístění (země) a poskytuje počet zákazníků v každé skupině. Výsledky jsou seřazené podle názvu země. Seskupené výsledky jsou seřazené podle název města.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
