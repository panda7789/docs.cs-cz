---
ms.openlocfilehash: a4b8a03661650a3ef1d96b656798c3c3d39a5705
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58467077"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží `localhost` selže

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží <code>localhost</code> selže s chybou, &quot;při navazování připojení k serveru SQL Server došlo k chybě související se sítí nebo s instancí. Server nebyl nalezen nebo nebyl přístupný. Ověřte, zda je název instance správný a, SQL Server je nakonfigurován pro povolit vzdálená připojení. (poskytovatel: Rozhraní sítě systému SQL, chyba: 26 - Chyba při vyhledávání zadaného serveru či Instance)&quot;|
|Doporučení|Tento problém byl vyřešen a obnovit předchozí chování v rozhraní .NET Framework 4.6.2. Pro připojení k databázi SQL serveru, který se přeloží <code>localhost</code>, proveďte upgrade na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Modul runtime|

