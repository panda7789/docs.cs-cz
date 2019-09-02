---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205153"
---
# <a name="creating-a-dataset"></a>Vytvoření datové sady
Vytvoříte instanci <xref:System.Data.DataSet> <xref:System.Data.DataSet> voláním konstruktoru. Volitelně můžete zadat argument name. Pokud neurčíte název pro <xref:System.Data.DataSet>, název je nastaven na "NewDataSet".  
  
 Můžete také vytvořit novou <xref:System.Data.DataSet> na základě existujícího. <xref:System.Data.DataSet> <xref:System.Data.DataSet> Nový může být přesná kopie stávajícího <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, který kopíruje relační strukturu nebo schéma, ale neobsahuje žádná data z existujících <xref:System.Data.DataSet>nebo podmnožinu <xref:System.Data.DataSet>, obsahuje pouze upravené řádky z existující <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> pomocí metody. Další informace najdete v tématu [kopírování obsahu datové sady](copying-dataset-contents.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Viz také:

- [Naplnění datové sady z adaptéru dat](../populating-a-dataset-from-a-dataadapter.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
