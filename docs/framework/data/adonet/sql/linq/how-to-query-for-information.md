---
title: 'Postupy: dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634648"
---
# <a name="how-to-query-for-information"></a>Postupy: dotaz na informace
Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používají stejnou syntaxi jako dotazy v LINQ. Jediným rozdílem je, že objekty odkazované v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou namapovány na prvky v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování.  
  
 Některé funkce dotazů LINQ mohou vyžadovat zvláštní pozornost v aplikacích [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Další informace najdete v tématu [Koncepty dotazů](query-concepts.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz požádá o seznam zákazníků z Londýna. V tomto příkladu je `Customers` tabulka v ukázkové databázi Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření objektového modelu](creating-the-object-model.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Dotazování na databázi](querying-the-database.md)
