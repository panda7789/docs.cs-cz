---
title: Trasování data v ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 1b2ee679ce4b0d39b993b9081f428fe585ef7d92
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784891"
---
# <a name="data-tracing-in-adonet"></a>Trasování data v ADO.NET

Služba ADO.NET nabízí integrované funkce pro trasování dat, které podporují poskytovatelé dat .NET pro SQL Server, Oracle, OLE DB a rozhraní ODBC, a také rozhraní ADO.NET <xref:System.Data.DataSet>a SQL Server síťové protokoly.

Trasování volání rozhraní API pro přístup k datům může pomáhat diagnostikovat následující problémy:

- Neshoda schémat mezi klientským programem a databází.

- Problémy nedostupnosti databáze nebo síťové knihovny.

- Nesprávný kód SQL, ať už pevně kódovaný nebo generovaný aplikací.

- Nesprávná programovací logika

- Problémy vyplývající z interakce mezi několika komponentami ADO.NET nebo mezi ADO.NET a vašimi vlastními komponentami

Pro podporu různých trasovacích technologií je trasování rozšiřitelné, takže vývojář může sledovat problém na libovolné úrovni aplikačního zásobníku. I když trasování není funkce jenom ADO.NET, poskytovatelé Microsoftu využívají zobecněná rozhraní API pro sledování a instrumentaci.

Další informace o nastavení a konfiguraci spravovaného trasování v ADO.NET najdete v tématu věnovaném [trasování přístupových dat](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Přístup k diagnostickým informacím v protokolu rozšířených událostí

V .NET Framework Zprostředkovatel dat pro SQL Server bylo aktualizováno trasování přístupu k datům ([trasování přístupu k datům](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))), aby bylo snazší zjednodušit korelaci klientských událostí s diagnostickými informacemi, jako je například selhání připojení, z připojení serveru. informace o výkonu kruhové vyrovnávací paměti a aplikace v protokolu rozšířených událostí. Informace o čtení protokolu rozšířených událostí najdete v tématu [zobrazení dat relace události](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Pro operace připojení pošle ADO.NET ID připojení klienta. Pokud připojení selže, můžete získat přístup k vyrovnávací paměti vyzvánění připojení ([řešení potíží s připojením v SQL Server 2008 s cyklickou vyrovnávací pamětí připojení](https://go.microsoft.com/fwlink/?LinkId=207752)) a najít `ClientConnectionID` pole a získat diagnostické informace o selhání připojení. ID připojení klienta se zaznamenávají do vyrovnávací paměti prstence pouze v případě, že dojde k chybě. (Pokud připojení selže před odesláním paketu před přihlášením, nebude vygenerováno ID připojení klienta.) ID připojení klienta je 16bitový identifikátor GUID. Pokud `client_connection_id` je akce přidána do událostí v relaci rozšířené události, můžete také vyhledat ID připojení klienta ve výstupu rozšířené události. Pokud potřebujete další diagnostickou pomoc klientského ovladače, můžete povolit trasování přístupu k `ClientConnectionID` datům a znovu spustit příkaz pro připojení a sledovat pole v trasování přístupu k datům.

ID připojení klienta můžete získat programově pomocí `SqlConnection.ClientConnectionID` vlastnosti.

Je k dispozici <xref:System.Data.SqlClient.SqlConnection> pro objekt, který úspěšně naváže připojení. `ClientConnectionID` Pokud se pokus o připojení nezdaří `ClientConnectionID` , může být k `SqlException.ToString`dispozici prostřednictvím.

ADO.NET také odesílá ID aktivity specifické pro vlákno. ID aktivity se zachycuje v relacích rozšířených událostí, pokud jsou relace spuštěné s povolenou možností TRACK_CAUSALITY. V případě problémů s výkonem s aktivním připojením můžete získat ID aktivity z trasování (`ActivityID` pole) klienta pro přístup k datům a potom najít ID aktivity ve výstupu rozšířených událostí. ID aktivity v rozšířených událostech je 16bitový identifikátor GUID (nejedná se o stejný identifikátor GUID pro ID připojení klienta) připojený pomocí čísla sekvence se čtyřmi bajty. Pořadové číslo představuje pořadí žádosti v rámci vlákna a označuje relativní pořadí příkazů Batch a RPC pro vlákno. V `ActivityID` tuto chvíli se volitelně posílá příkazy služby SQL Batch a požadavky RPC, když je zapnuté trasování přístupu k datům, a 18 bit v konfiguraci trasování přístupu k datům.

Následuje ukázka, který pomocí jazyka Transact-SQL spustí relaci rozšířených událostí, která bude uložená v kruhové vyrovnávací paměti, a poznamenejte si ID aktivity odeslané z klienta na RPC a dávkové operace.

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

- [Trasování sítě v rozhraní .NET Framework](../../network-programming/network-tracing.md)
- [Trasování a instrumentace aplikací](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Přehled ADO.NET](ado-net-overview.md)
