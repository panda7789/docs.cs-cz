---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997590"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikace publikované pomocí ClickOnce, které používají certifikát SHA-256, můžou selhat ve Windows 2003

|   |   |
|---|---|
|Podrobnosti|Spustitelný soubor je podepsaný pomocí SHA256. Dříve byla podepsána pomocí SHA1 bez ohledu na to, zda byl certifikát pro podpis kódu SHA-1 nebo SHA-256. To platí pro:<ul><li>Všechny aplikace vytvořené pomocí sady Visual Studio 2012 nebo novější.</li><li>Aplikace vytvořené pomocí sady Visual Studio 2010 nebo starší v systémech s .NET Framework 4,5 k dispozici.</li></ul>Kromě toho, pokud je k dispozici .NET Framework 4,5 nebo novější, manifest ClickOnce je také podepsán pomocí algoritmu SHA-256 pro certifikáty SHA-256 bez ohledu na .NET Framework verzi, proti které byla zkompilována.|
|Doporučení|Změna v podepisování spustitelného souboru ClickOnce ovlivní pouze systémy Windows Server 2003; vyžadují instalaci znalostní báze KB 938397. Změna v podepisování manifestu pomocí SHA-256 i v případě, že aplikace cílí na .NET Framework 4,0 nebo starší verze představuje závislost modulu runtime na .NET Framework 4,5 nebo novější verze.|
|Scope|Edge|
|Version|4.5|
|type|Změna cílení|
