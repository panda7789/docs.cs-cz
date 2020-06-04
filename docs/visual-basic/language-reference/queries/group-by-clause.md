---
title: Group By – klauzule
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
ms.openlocfilehash: 5fce4f818e22373de7f1b37b941fd88155f3a33f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359887"
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
  
     Nepovinný parametr. Jedno nebo více polí proměnné nebo proměnných dotazu, které explicitně identifikují pole, která mají být součástí seskupeného výsledku. Nejsou-li zadána žádná pole, jsou v seskupeném výsledku obsažena všechna pole proměnné dotazu nebo proměnné.  
  
- `keyExp1`  
  
     Povinná hodnota. Výraz, který identifikuje klíč, který se má použít k určení skupin prvků. Můžete zadat více než jeden klíč, který určí složený klíč.  
  
- `keyExp2`  
  
     Nepovinný parametr. Jeden nebo více dalších klíčů, které jsou kombinovány s nástrojem `keyExp1` k vytvoření složeného klíče.  
  
- `aggregateList`  
  
     Povinná hodnota. Jeden nebo více výrazů, které identifikují způsob agregace skupin. Chcete-li identifikovat název člena pro seskupené výsledky, použijte `Group` klíčové slovo, které může být v jednom z následujících forem:  
  
    ```vb  
    Into Group  
    ```  
  
     -nebo-  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.  
  
## <a name="remarks"></a>Poznámky  
 Klauzuli můžete použít `Group By` k přerušení výsledků dotazu do skupin. Seskupení je založeno na klíči nebo složeném klíči, který se skládá z více klíčů. Prvky, které jsou přidruženy k odpovídajícím hodnotám klíčů, jsou zahrnuty ve stejné skupině.  
  
 Použijete `aggregateList` parametr `Into` klauzule a `Group` klíčové slovo k identifikaci názvu člena, který se používá k odkazování na skupinu. Můžete také zahrnout agregační funkce v `Into` klauzuli pro výpočet hodnot pro seskupené prvky. Seznam standardních agregačních funkcí naleznete v tématu [klauzule Aggregate](aggregate-clause.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu seskupuje seznam zákazníků na základě jejich umístění (země/oblast) a poskytuje počet zákazníků v každé skupině. Výsledky jsou seřazené podle názvu země nebo oblasti. Seskupené výsledky jsou seřazené podle názvu města.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Order By – klauzule](order-by-clause.md)
- [Aggregate – klauzule](aggregate-clause.md)
- [Group Join – klauzule](group-join-clause.md)
