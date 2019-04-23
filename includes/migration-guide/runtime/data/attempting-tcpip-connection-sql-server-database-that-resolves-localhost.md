---
ms.openlocfilehash: 88d6c166acf9e9ab72c2713b575a8453779f70d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774142"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží `localhost` selže

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží <code>localhost</code> selže s chybou, &quot;při navazování připojení k serveru SQL Server došlo k chybě související se sítí nebo s instancí. Server nebyl nalezen nebo nebyl přístupný. Ověřte, zda je název instance správný a, SQL Server je nakonfigurován pro povolit vzdálená připojení. (poskytovatel: Rozhraní sítě systému SQL, chyba: 26 - Chyba při vyhledávání zadaného serveru či Instance)&quot;|
|Doporučení|Tento problém byl vyřešen a obnovit předchozí chování v rozhraní .NET Framework 4.6.2. Pro připojení k databázi SQL serveru, který se přeloží <code>localhost</code>, proveďte upgrade na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Modul runtime|
