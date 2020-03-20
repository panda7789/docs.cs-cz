---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887752"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash nyní vrátí false pro všechny selhání ověření

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.2 vrátí tato metoda **hodnotu False,** pokud je samotný podpis špatně formátován. Nyní vrátí false pro všechny selhání ověření. V rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> metoda vyvolá, pokud samotný podpis je špatně formátován.|
|Návrh|Jakýkoli kód, jehož <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> spuštění závisí na zpracování by místo toho spustit, pokud ověření selže a metoda vrátí **False**.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
