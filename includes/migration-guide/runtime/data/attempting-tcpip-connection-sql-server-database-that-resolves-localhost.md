---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237850"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Pokus o připojení protokolu TCP/IP k databázi `localhost` serveru SQL Server, která se překládá k selhání

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 došlo při navazování připojení k <code>localhost</code> serveru SQL &quot;Server k databázi serveru SQL Server, která se s chybou řeší na selhání, došlo při navazování připojení k serveru SQL Server k chybě související se sítí nebo instancí. Server se nenašel nebo nebyl dostupný. Ověřte, zda je název instance správný a zda je server SQL Server nakonfigurován tak, aby umožňoval vzdálená připojení. (poskytovatel: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;|
|Návrh|Tento problém byl vyřešen a předchozí chování obnoveno v rozhraní .NET Framework 4.6.2. Chcete-li se připojit k datové části serveru <code>localhost</code>SQL Server, která se překládá na , upgradujte na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
