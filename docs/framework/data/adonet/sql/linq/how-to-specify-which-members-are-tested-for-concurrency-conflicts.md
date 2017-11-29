---
title: "Postupy: Zadejte, kteří členové jsou testovány konflikty souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c13c5d6578f27155b87744ed8730f5fae2e1e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Postupy: Zadejte, kteří členové jsou testovány konflikty souběžnosti
Používání jedné do tří výčty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> kontroluje atribut k určení členy, které mají být zahrnuty v aktualizaci pro zjišťování konfliktů optimistickou metodu souběžného.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Vlastnost (mapovat v době návrhu) se používá spolu s funkcí concurrency Runtime v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Původní hodnoty členů jsou porovnávány s aktuálním stavem databáze, tak dlouho, dokud žádné je označena jako `IsVersion=true`. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Vždy nutné použít tento člen pro zjišťování konfliktů  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnotu vlastnosti na `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Nikdy používat tento člen pro zjišťování konfliktů  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnotu vlastnosti na `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Chcete-li použít tento člen pro zjišťování konfliktů, pouze v případě, že aplikace byla změněna hodnota člena  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnotu vlastnosti na `WhenChanged`.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, že `HomePage` objekty by měl být vůbec neotestovali během kontroly aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa je v konfliktu změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
