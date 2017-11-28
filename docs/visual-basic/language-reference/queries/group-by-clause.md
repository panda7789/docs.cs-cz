---
title: "Group By – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By – klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [AGGREGATE – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md)
