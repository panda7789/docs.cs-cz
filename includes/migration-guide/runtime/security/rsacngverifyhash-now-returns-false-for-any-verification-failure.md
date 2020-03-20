---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887752"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="db933-101">RSACng.VerifyHash nyní vrátí false pro všechny selhání ověření</span><span class="sxs-lookup"><span data-stu-id="db933-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="db933-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="db933-102">Details</span></span>|<span data-ttu-id="db933-103">Počínaje rozhraním .NET Framework 4.6.2 vrátí tato metoda **hodnotu False,** pokud je samotný podpis špatně formátován.</span><span class="sxs-lookup"><span data-stu-id="db933-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="db933-104">Nyní vrátí false pro všechny selhání ověření. V rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> metoda vyvolá, pokud samotný podpis je špatně formátován.</span><span class="sxs-lookup"><span data-stu-id="db933-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="db933-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="db933-105">Suggestion</span></span>|<span data-ttu-id="db933-106">Jakýkoli kód, jehož <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> spuštění závisí na zpracování by místo toho spustit, pokud ověření selže a metoda vrátí **False**.</span><span class="sxs-lookup"><span data-stu-id="db933-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="db933-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="db933-107">Scope</span></span>|<span data-ttu-id="db933-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="db933-108">Minor</span></span>|
|<span data-ttu-id="db933-109">Version</span><span class="sxs-lookup"><span data-stu-id="db933-109">Version</span></span>|<span data-ttu-id="db933-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="db933-110">4.6.2</span></span>|
|<span data-ttu-id="db933-111">Typ</span><span class="sxs-lookup"><span data-stu-id="db933-111">Type</span></span>|<span data-ttu-id="db933-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="db933-112">Runtime</span></span>|
|<span data-ttu-id="db933-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="db933-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
