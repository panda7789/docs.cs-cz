---
title: Trasování data v ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: df49fc7a5f7c437132a4dc24ed7f18492d9e7647
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583777"
---
# <a name="data-tracing-in-adonet"></a>Trasování data v ADO.NET

ADO.NET obsahuje předdefinované datové funkce sledování, je podporován zprostředkovatele dat .NET pro SQL Server, Oracle, OLE DB a rozhraní ODBC, jakož i ADO.NET <xref:System.Data.DataSet>a protokoly sítě systému SQL Server.

Data trasování volání rozhraní API přístup může pomoci diagnostikovat následující problémy:

- Neshoda schémat mezi klientskou aplikaci a databázi.

- Databáze nedostupnost nebo síťové knihovny problémy.

- Nesprávný SQL pevně zakódované nebo generovaných aplikací.

- Nesprávný programovou logiku.

- Problémy s vyplývající z interakce mezi více komponent ADO.NET nebo mezi ADO.NET a vlastní komponenty.

Pro podporu různých trasování technologií, je rozšiřitelný, trasování, takže vývojáři můžou sledovat potíže na libovolné úrovni zásobníku aplikací. I když trasování není funkce jen pro ADO.NET, poskytovatelé Microsoftu využít výhod zobecněný trasování a instrumentace rozhraní API.

Další informace o nastavení a konfigurace spravovaných trasování v ADO.NET, naleznete v tématu [přístup k datům trasování](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Přístup k diagnostickým informacím v rozšířené události protokolu

V rámci .NET Data Provider pro SQL Server, pro přístup k datům trasování ([trasování Data Access](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) byl aktualizován, aby bylo snazší usnadňuje korelaci událostí klienta s diagnostickými informacemi, jako jsou selhání připojení z připojení k serveru na cyklické vyrovnávací paměti a výkonu informace o aplikacích v rozšířené události protokolu. Informace o čtení rozšířené události protokolu najdete v tématu [zobrazit Data relace události](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Pro operace připojení ADO.NET pošle klient ID připojení. Pokud se nepovede, může přístup k připojení k cyklické vyrovnávací paměti ([v systému SQL Server 2008 s cyklické vyrovnávací paměti připojení k řešení potíží s připojením](https://go.microsoft.com/fwlink/?LinkId=207752)) a najděte `ClientConnectionID` pole a získání diagnostických informací připojení se nezdařilo. ID připojení klientů jsou protokolovány v cyklické vyrovnávací paměti pouze v případě, že dojde k chybě. (Neúspěšné připojení před odesláním paketu hodnoty ID připojení klienta nevygeneruje.) ID připojení klienta je identifikátor GUID 16 bajtů. Můžete také vyhledat připojení klienta ID v výstup cíle rozšířeného počtu událostí, pokud `client_connection_id` akce se přidá na události v relaci rozšířených událostí. Můžete povolit trasování data access a znovu spusťte příkaz připojení a sledujte `ClientConnectionID` pole přístup do dat trasování, pokud potřebujete další pomoc diagnostických ovladače klienta.

Klienta můžete získat ID připojení prostřednictvím kódu programu pomocí `SqlConnection.ClientConnectionID` vlastnost.

`ClientConnectionID` Je k dispozici pro <xref:System.Data.SqlClient.SqlConnection> objekt, který úspěšně naváže připojení. Pokud se nezdaří pokus o připojení, `ClientConnectionID` může být k dispozici prostřednictvím `SqlException.ToString`.

ADO.NET rovněž odesílá ID aktivity specifické pro vlákno. ID aktivity je zachycena v relace rozšířených událostí, pokud relace se spustí s povolenou možností TRACK_CAUSALITY. Pro problémy s výkonem s aktivním připojení, můžete získat ID aktivity sledování přístupu dat klienta (`ActivityID` pole) a vyhledejte ID aktivity ve výstupu rozšířené události. ID aktivity v rozšířených událostí je 16 bajtů identifikátor GUID (není stejný jako identifikátor GUID pro připojení ID klienta) s čtyř bajtů pořadové číslo. Pořadové číslo představuje pořadí požadavku v rámci vlákno a určuje relativní řazení služby batch a příkazy vzdáleného volání Procedur vlákna. `ActivityID` Se aktuálně volitelně odešle pro dávkové příkazy SQL a žádosti RPC, když je povoleno trasování přístupu dat na a 18 bitu v přístupu k datům konfigurace slovo trasování je zapnuté.

Tady je ukázka, která používá [!INCLUDE[tsql](../../../../includes/tsql-md.md)] spustit relaci rozšířených událostí, které se uloží na cyklické vyrovnávací paměti a zaznamená ID aktivity odeslat z klienta na vzdálené volání Procedur a dávkové operace.

```sql
create event session MySession on server
add event connectivity_ring_buffer_recorded,
add event sql_statement_starting (action (client_connection_id)),
add event sql_statement_completed (action (client_connection_id)),
add event rpc_starting (action (client_connection_id)),
add event rpc_completed (action (client_connection_id))
add target ring_buffer with (track_causality=on)
```

## <a name="see-also"></a>Viz také:

- [Trasování sítě v rozhraní .NET Framework](../../../../docs/framework/network-programming/network-tracing.md)
- [Trasování a instrumentace aplikací](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
