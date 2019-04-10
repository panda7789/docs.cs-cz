---
title: 'Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 9a1b4ab2dc28c569473eddbf50b96d10298d8d3c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310431"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti
Používání jedné do tří výčtů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> zkontroluje atribut k určení, které členy mají být zahrnuty v aktualizaci pro zjišťování konfliktů optimistického řízení souběžnosti.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Vlastnost (namapované v době návrhu) se používá spolu s funkcí concurrency Runtime v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Původní hodnoty členů jsou porovnány s aktuálním stavem databáze, tak dlouho, dokud žádný člen je určený jako `IsVersion=true`. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Tento člen vždy používat zjišťování konfliktů  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnoty vlastnosti `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Tento člen nikdy používat zjišťování konfliktů  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnoty vlastnosti `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Chcete-li použít tento člen pro zjišťování konfliktů, pouze v případě, že aplikace byla změněna hodnota člena  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> hodnoty vlastnosti `WhenChanged`.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, že `HomePage` objektů by měl být testován nikdy během kontroly aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
