---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786503"
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
- [Přehled ADO.NET](../ado-net-overview.md)
