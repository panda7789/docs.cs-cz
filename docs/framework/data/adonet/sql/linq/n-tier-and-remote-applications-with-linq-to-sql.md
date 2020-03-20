---
title: N-vrstvé a vzdálené aplikace s LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6758ae23c25d8e7a4255d0a784cccd1eb404bfe7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174300"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-vrstvé a vzdálené aplikace s LINQ to SQL
Můžete vytvořit n-vrstvé nebo vícevrstvé aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Kontext [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dat, třídy entit a logika konstrukce dotazu jsou obvykle umístěny na střední vrstvě jako vrstva přístupu k datům (DAL). Obchodní logiku a všechna netrvalá data mohou být implementována zcela v částečných třídách a metodách entit a kontextu dat nebo mohou být implementovány v samostatných třídách.

 Klientská nebo prezentační vrstva volá metody na vzdáleném rozhraní střední vrstvy a DAL na <xref:System.Data.Linq.DataContext> této vrstvě bude spouštět dotazy nebo uložené procedury, které jsou mapovány na metody. Střední vrstva vrátí data klientům obvykle jako reprezentace XML entit nebo proxy objektů.

 Na střední vrstvě entity jsou vytvořeny kontext dat, který sleduje jejich stav a spravuje odložené načítání z a odesílání změn do databáze. Tyto entity jsou "připojeny" `DataContext`k . Však po entity jsou odeslány do jiné vrstvy prostřednictvím `DataContext` serializace, stanou odpojené, což znamená, že již sledování jejich stavu. Entity, které klient odešle zpět pro aktualizace, musí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] být znovu připojeny k kontextu dat, než bude možné odeslat změny do databáze. Klient je zodpovědný za poskytování původní hodnoty nebo časová razítka zpět do střední vrstvy, pokud jsou požadovány pro optimistické kontroly souběžnosti.

 V ASP.NET aplikací <xref:System.Web.UI.WebControls.LinqDataSource> spravuje většinu této složitosti. Další informace naleznete v tématu [Přehled ovládacího prvku webového serveru LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Další zdroje
 Další informace o implementaci n-vrstvých [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aplikací, které používají , naleznete v následujících tématech:

- [N-vrstvé nastavení LINQ to SQL s ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [N-vrstvé nastavení LINQ to SQL s webovými službami](linq-to-sql-n-tier-with-web-services.md)

- [Implementace N-vrstvé obchodní logiky](implementing-business-logic-linq-to-sql.md)

- [Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Další informace o n-vrstvých aplikacích, které používají ADO.NET datových sad, naleznete [v tématu Práce s datovými sadami v n-vrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Viz také

- [Základní informace](background-information.md)
