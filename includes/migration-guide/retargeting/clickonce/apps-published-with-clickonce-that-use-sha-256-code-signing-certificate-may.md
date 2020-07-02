---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615635"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikace publikované pomocí ClickOnce, které používají certifikát SHA-256, můžou selhat ve Windows 2003

#### <a name="details"></a>Podrobnosti

Spustitelný soubor je podepsaný pomocí SHA256. Dříve byla podepsána pomocí SHA1 bez ohledu na to, zda byl certifikát pro podpis kódu SHA-1 nebo SHA-256. To platí pro:

- Všechny aplikace vytvořené pomocí sady Visual Studio 2012 nebo novější.
- Aplikace vytvořené pomocí sady Visual Studio 2010 nebo starší v systémech s .NET Framework 4,5 k dispozici.
Kromě toho, pokud je k dispozici .NET Framework 4,5 nebo novější, manifest ClickOnce je také podepsán pomocí algoritmu SHA-256 pro certifikáty SHA-256 bez ohledu na .NET Framework verzi, proti které byla zkompilována.

#### <a name="suggestion"></a>Návrh

Změna v podepisování spustitelného souboru ClickOnce ovlivní pouze systémy Windows Server 2003; vyžadují instalaci znalostní báze KB 938397. Změna v podepisování manifestu pomocí SHA-256 i v případě, že aplikace cílí na .NET Framework 4,0 nebo starší verze představuje závislost modulu runtime na .NET Framework 4,5 nebo novější verze.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5         |
| Typ    | Změna cílení |
