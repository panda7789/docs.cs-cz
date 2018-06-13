---
title: Technologie LINQ to SQL N-vrstvá s technologií ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 435f24a0f105a24bbec91a7e70dc5aaaa25e5649
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360235"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Technologie LINQ to SQL N-vrstvá s technologií ASP.NET
V [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru. Ovládací prvek zpracovává většinu logiky, která musí mít k dotazu vůči [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], předejte data do prohlížeče, jejich načtení a odešlete ji do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> který pak aktualizuje databázi. Stačí pouze nakonfigurovat ovládacího prvku do kódu a ovládací prvek zpracovává všechny přenos dat mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a v prohlížeči. Protože ovládací prvek zpracovává interakce s prezentační vrstvou a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává komunikaci se službou datové vrstvy, váš hlavní výběr v [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] vícevrstvé aplikace se na psaní vlastní obchodní logiku.  
  
 Další informace o `LINQDataSource`, najdete v části [NIB: Přehled ovládacího prvku webového serveru LinqDataSource](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Viz také  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
