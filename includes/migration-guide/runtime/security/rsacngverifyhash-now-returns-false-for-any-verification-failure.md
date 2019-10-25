---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887752"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="dc34e-101">Algoritmem RSACng. VerifyHash teď pro jakékoli selhání ověřování vrátí hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="dc34e-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dc34e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dc34e-102">Details</span></span>|<span data-ttu-id="dc34e-103">Počínaje .NET Framework 4.6.2 vrátí tato metoda **hodnotu false** , pokud samotný podpis není správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="dc34e-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="dc34e-104">Nyní vrátí hodnotu false pro jakékoli selhání ověřování. V .NET Framework 4,6 a 4.6.1 metoda vyvolá <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>, pokud samotný podpis není správně naformátován.</span><span class="sxs-lookup"><span data-stu-id="dc34e-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="dc34e-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="dc34e-105">Suggestion</span></span>|<span data-ttu-id="dc34e-106">Jakýkoli kód, jehož provádění závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> je třeba provést, pokud se ověření nepovede a metoda vrátí **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="dc34e-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="dc34e-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="dc34e-107">Scope</span></span>|<span data-ttu-id="dc34e-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="dc34e-108">Minor</span></span>|
|<span data-ttu-id="dc34e-109">Version</span><span class="sxs-lookup"><span data-stu-id="dc34e-109">Version</span></span>|<span data-ttu-id="dc34e-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="dc34e-110">4.6.2</span></span>|
|<span data-ttu-id="dc34e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="dc34e-111">Type</span></span>|<span data-ttu-id="dc34e-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="dc34e-112">Runtime</span></span>|
|<span data-ttu-id="dc34e-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dc34e-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
