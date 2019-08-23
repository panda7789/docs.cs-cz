---
title: 'Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: fc6fafa474805c2644bb2deabdceed192776ac76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938757"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti
Použijte jeden ze tří výčtů na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost u <xref:System.Data.Linq.Mapping.ColumnAttribute> atributu k určení, které členy mají být zahrnuty do kontrol aktualizací pro detekci konfliktů optimistického souběžnosti.  
  
 Vlastnost (mapovaná v době návrhu) se používá společně s funkcemi souběžného běhu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Další informace najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Hodnoty původních členů jsou porovnány s aktuálním stavem databáze, pokud není určen `IsVersion=true`žádný člen. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Vždy používat tohoto člena k detekci konfliktů  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. `Always`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Nikdy nepoužívat tohoto člena k detekci konfliktů  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. `Never`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Použití tohoto člena pro zjištění konfliktů pouze v případě, že aplikace změnila hodnotu člena  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. `WhenChanged`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, že `HomePage` objekty by nikdy neměly být testovány během kontrol aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
