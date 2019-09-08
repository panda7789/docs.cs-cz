---
title: N-vrstvé nastavení LINQ to SQL s ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793036"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>N-vrstvé nastavení LINQ to SQL s ASP.NET
V aplikacích ASP.NET, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]používají, <xref:System.Web.UI.WebControls.LinqDataSource> použijte ovládací prvek webového serveru. Ovládací prvek zpracovává většinu logiky, které musí mít dotaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]na, předat data do prohlížeče, načíst je a odeslat je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> do nástroje, který pak aktualizuje databázi. Pouze nakonfigurujete ovládací prvek v kódu a ovládací prvek zpracovává veškerou přenos dat mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a prohlížečem. Vzhledem k tomu, že ovládací prvek zpracovává interakce s prezentační vrstvou a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává komunikaci s datovou vrstvou, hlavní fokus v ASP.NETch aplikacích je při psaní vlastní obchodní logiky.  
  
 Další informace o `LINQDataSource`naleznete v tématu [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
