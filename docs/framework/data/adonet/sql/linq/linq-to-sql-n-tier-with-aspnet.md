---
title: Technologie LINQ to SQL. N-vrstvou pomocí technologie ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: b85392408d2fa62c481381c5028e228f280a1dc8
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093649"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Technologie LINQ to SQL. N-vrstvou pomocí technologie ASP.NET
V [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru. Ovládací prvek zpracovává většinu logiku, která musí mít k dotazu vůči [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], předejte data do prohlížeče, načíst a odeslat ho do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> který pak zaktualizuje databázi. Stačí pouze nakonfigurovat ovládací prvek ve značkách a ovládací prvek zpracovává všechny datové přenosy mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a prohlížečem. Vzhledem k tomu, že ovládací prvek zpracovává interakce s prezentační vrstva a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává vnitřní komunikaci s datovou vrstvou, hlavní fokus v [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] vícevrstvé aplikace je na vaše vlastní obchodní logiky.  
  
 Další informace o `LINQDataSource`, naleznete v tématu [Přehled ovládacího prvku webového serveru zdroje dat LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:
- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
