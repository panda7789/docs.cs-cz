---
title: N-vrstvé a vzdálené aplikace s LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 94ca057da10c3570e85e17b5caec2d86154d8a3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781414"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-vrstvé a vzdálené aplikace s LINQ to SQL
Můžete vytvářet n-vrstvé a vícevrstvé aplikace, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]používají. Obvykle se datový kontext, třídy entit a logika vytváření dotazů nacházejí na střední úrovni jako vrstva přístupu k datům (dal). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Obchodní logika a jakákoli netrvalá data lze implementovat zcela v částečných třídách a metodách entit a kontextu dat, nebo je lze implementovat do samostatných tříd.

 Klient nebo prezentační vrstva volá metody ve vzdáleném rozhraní střední vrstvy a dal na této úrovni spustí dotazy nebo uložené procedury, které jsou namapovány na <xref:System.Data.Linq.DataContext> metody. Střední úroveň vrátí data klientům obvykle jako reprezentace XML entit nebo objektů proxy.

 Na střední úrovni jsou entity vytvořeny pomocí kontextu dat, který sleduje jejich stav a spravuje odložené načtení a odeslání změn do databáze. Tyto entity jsou "připojené" k `DataContext`. Po odeslání entit do jiné úrovně prostřednictvím serializace však dojde k jejich odpojení, což znamená, že `DataContext` již nebude sledovat jejich stav. Entity, které klient odesílá zpět pro aktualizace, musí být před [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] odesláním změn do databáze znovu připojeny k datovému kontextu. Klient zodpovídá za poskytnutí původních hodnot nebo časových razítek zpět do střední vrstvy, pokud jsou vyžadovány pro optimistické kontroly souběžnosti.

 V aplikacích <xref:System.Web.UI.WebControls.LinqDataSource> ASP.NET spravuje většinu této složitosti. Další informace naleznete v tématu [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Další prostředky
 Další informace o implementaci n-vrstvých aplikací, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], najdete v následujících tématech:

- [N-vrstvé nastavení LINQ to SQL s ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [N-vrstvé nastavení LINQ to SQL s webovými službami](linq-to-sql-n-tier-with-web-services.md) 

- [Implementace N-vrstvé obchodní logiky](implementing-business-logic-linq-to-sql.md)

- [Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Další informace o n-vrstvých aplikacích, které používají ADO.NET datové sady, najdete v tématu [práce s datovými sadami v n-vrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
