---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621782"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Pokus o připojení TCP/IP k databázi SQL Server, která se překládá na `localhost` neúspěšné

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,6 a 4.6.1 se při pokusu o připojení TCP/IP k databázi SQL Server, která překládá na chybu <code>localhost</code> , nezdařila chyba, &quot; došlo k chybě související se sítí nebo instancí při navazování připojení k SQL Server. Server se nenašel nebo nebyl dostupný. Ověřte, zda je název instance správný a zda je SQL Server nakonfigurovaná tak, aby povolovala vzdálená připojení. (poskytovatel: síťová rozhraní SQL, chyba: 26 – Chyba při hledání zadaného serveru nebo instance)&quot;

#### <a name="suggestion"></a>Návrh

Tento problém byl vyřešen a předchozí chování obnoveno ve .NET Framework 4.6.2. Pokud se chcete připojit k databázi SQL Server, na kterou se překládá <code>localhost</code> , upgradujte na .NET Framework 4.6.2.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime|
