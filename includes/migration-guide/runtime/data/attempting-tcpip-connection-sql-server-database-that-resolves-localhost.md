---
ms.openlocfilehash: 8ac6d50b192001f6d924b2ffe4a367a33fc2c689
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857477"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží `localhost` selže

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží <code>localhost</code> selže s chybou, &quot;při navazování připojení k serveru SQL Server došlo k chybě související se sítí nebo s instancí. Server nebyl nalezen nebo nebyl přístupný. Ověřte, zda je název instance správný a, SQL Server je nakonfigurován pro povolit vzdálená připojení. (poskytovatel: Rozhraní sítě systému SQL, chyba: 26 - Chyba při vyhledávání zadaného serveru či Instance)&quot;|
|Doporučení|Tento problém byl vyřešen a obnovit předchozí chování v rozhraní .NET Framework 4.6.2. Pro připojení k serveru SQL Server Database, který se přeloží na <code>localhost</code>, proveďte upgrade na rozhraní .NET Framework 4.6.2.|
|Scope|Vedlejší|
|Version|4.6|
|type|Modul runtime|

