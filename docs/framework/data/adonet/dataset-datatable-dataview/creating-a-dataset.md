---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 43e2f7a1892459ca96d44350431935493b596a60
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509548"
---
# <a name="creating-a-dataset"></a>Vytvoření datové sady
Vytvoření instance <xref:System.Data.DataSet> voláním <xref:System.Data.DataSet> konstruktoru. Volitelně můžete zadáte název argumentu. Pokud nezadáte název <xref:System.Data.DataSet>, je název nastavený na "NewDataSet".  
  
 Můžete také vytvořit novou <xref:System.Data.DataSet> založené na existujícím <xref:System.Data.DataSet>. Nové <xref:System.Data.DataSet> může být přesnou kopii existující <xref:System.Data.DataSet>; klon <xref:System.Data.DataSet> , která kopíruje relační struktury nebo schématu, ale která neobsahuje žádný dat z existující <xref:System.Data.DataSet>; nebo podmnožinu <xref:System.Data.DataSet>, obsahující jenom změněné řádky z existující <xref:System.Data.DataSet> pomocí <xref:System.Data.DataSet.GetChanges%2A> metody. Další informace najdete v tématu [kopírování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Viz také  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
