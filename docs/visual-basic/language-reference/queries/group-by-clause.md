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
ms.openlocfilehash: 8b3a480c226debc529c268e83437d15192592bd3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004751"
---
# <a name="group-by-clause-visual-basic"></a>Group By – klauzule (Visual Basic)
Seskupí prvky výsledku dotazu. Lze také použít k aplikování agregačních funkcí na každou skupinu. Operace seskupení je založena na jednom nebo více klíčích.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Součásti  
  
- `listField1`, `listField2`  
  
     Volitelné. Jedno nebo více polí proměnné nebo proměnných dotazu, které explicitně identifikují pole, která mají být součástí seskupeného výsledku. Nejsou-li zadána žádná pole, jsou v seskupeném výsledku obsažena všechna pole proměnné dotazu nebo proměnné.  
  
- `keyExp1`  
  
     Požadováno. Výraz, který identifikuje klíč, který se má použít k určení skupin prvků. Můžete zadat více než jeden klíč, který určí složený klíč.  
  
- `keyExp2`  
  
     Volitelné. Jeden nebo více dalších klíčů, které jsou kombinovány s `keyExp1` pro vytvoření složeného klíče.  
  
- `aggregateList`  
  
     Požadováno. Jeden nebo více výrazů, které identifikují způsob agregace skupin. Chcete-li identifikovat název člena pro seskupené výsledky, použijte klíčové slovo `Group`, které může být v jednom z následujících forem:  
  
    ```vb  
    Into Group  
    ```  
  
     -nebo-  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.  
  
## <a name="remarks"></a>Poznámky  
 K přerušení výsledků dotazu do skupin lze použít klauzuli `Group By`. Seskupení je založeno na klíči nebo složeném klíči, který se skládá z více klíčů. Prvky, které jsou přidruženy k odpovídajícím hodnotám klíčů, jsou zahrnuty ve stejné skupině.  
  
 Použijete parametr `aggregateList` klauzule `Into` a klíčové slovo `Group` k identifikaci názvu člena, který se používá k odkazování na skupinu. V klauzuli `Into` můžete také zahrnout agregační funkce pro výpočet hodnot seskupených prvků. Seznam standardních agregačních funkcí naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu seskupuje seznam zákazníků na základě jejich umístění (země/oblast) a poskytuje počet zákazníků v každé skupině. Výsledky jsou seřazené podle názvu země nebo oblasti. Seskupené výsledky jsou seřazené podle názvu města.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
