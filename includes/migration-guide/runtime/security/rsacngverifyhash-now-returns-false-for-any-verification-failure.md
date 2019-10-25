---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887752"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>Algoritmem RSACng. VerifyHash teď pro jakékoli selhání ověřování vrátí hodnotu false.

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6.2 vrátí tato metoda **hodnotu false** , pokud samotný podpis není správně naformátován. Nyní vrátí hodnotu false pro jakékoli selhání ověřování. V .NET Framework 4,6 a 4.6.1 metoda vyvolá <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>, pokud samotný podpis není správně naformátován.|
|Doporučení|Jakýkoli kód, jehož provádění závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> je třeba provést, pokud se ověření nepovede a metoda vrátí **hodnotu false**.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
