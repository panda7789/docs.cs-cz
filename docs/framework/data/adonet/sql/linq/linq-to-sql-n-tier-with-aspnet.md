---
title: Technologie LINQ to SQL. N-vrstvou pomocí technologie ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: e3cd5cfa34984080b0a2da418d6b6d35858053e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698684"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Technologie LINQ to SQL. N-vrstvou pomocí technologie ASP.NET
V [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru. Ovládací prvek zpracovává většinu logiku, která musí mít k dotazu vůči [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], předejte data do prohlížeče, načíst a odeslat ho do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> který pak zaktualizuje databázi. Stačí pouze nakonfigurovat ovládací prvek ve značkách a ovládací prvek zpracovává všechny datové přenosy mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a prohlížečem. Vzhledem k tomu, že ovládací prvek zpracovává interakce s prezentační vrstva a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává vnitřní komunikaci s datovou vrstvou, hlavní fokus v [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] vícevrstvé aplikace je na vaše vlastní obchodní logiky.  
  
 Další informace o `LINQDataSource`, naleznete v tématu [NIB: Přehled ovládacího prvku zdroje dat LinqDataSource webového serveru](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Viz také:
- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
