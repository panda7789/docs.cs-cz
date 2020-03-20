---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997590"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikace publikované pomocí funkce ClickOnce, které používají certifikát podepisování kódu SHA-256, mohou v systému Windows 2003 selhat.

|   |   |
|---|---|
|Podrobnosti|Spustitelný soubor je podepsán sha256. Dříve byl podepsán sha1 bez ohledu na to, zda certifikát podepisování kódu byl SHA-1 nebo SHA-256. To platí pro:<ul><li>Všechny aplikace vytvořené pomocí Visual Studia 2012 nebo novějšího.</li><li>Aplikace vytvořené pomocí sady Visual Studio 2010 nebo starší chodv systémy s rozhraním .NET Framework 4.5.</li></ul>Kromě toho pokud je k dispozici rozhraní .NET Framework 4.5 nebo novější, manifest ClickOnce je také podepsán sha-256 pro certifikáty SHA-256 bez ohledu na verzi rozhraní .NET Framework, proti které byl kompilován.|
|Návrh|Změna podepisování spustitelného souboru ClickOnce se týká pouze systémů windows server 2003. vyžadují instalaci KB 938397. Změna při podepisování manifestu pomocí SHA-256 i v případě, že aplikace cílí na rozhraní .NET Framework 4.0 nebo starší verze zavádí závislost za běhu na rozhraní .NET Framework 4.5 nebo novější verzi.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Změna cílení|
