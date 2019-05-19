---
title: N-vrstvé nastavení LINQ to SQL s ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 85ead36d1d927084c11dca1bd73a192b16e4ab7b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880757"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>N-vrstvé nastavení LINQ to SQL s ASP.NET
V aplikacích ASP.NET, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru. Ovládací prvek zpracovává většinu logiku, která musí mít k dotazu vůči [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], předejte data do prohlížeče, načíst a odeslat ho do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> který pak zaktualizuje databázi. Stačí pouze nakonfigurovat ovládací prvek ve značkách a ovládací prvek zpracovává všechny datové přenosy mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a prohlížečem. Vzhledem k tomu, že ovládací prvek zpracovává interakce s prezentační vrstva a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] popisovače je komunikace s datovou vrstvou, hlavní fokus v vícevrstvé aplikace ASP.NET na vaše vlastní obchodní logiky.  
  
 Další informace o `LINQDataSource`, naleznete v tématu [Přehled ovládacího prvku webového serveru zdroje dat LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
