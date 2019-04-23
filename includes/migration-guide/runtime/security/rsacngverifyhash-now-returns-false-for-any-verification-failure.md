---
ms.openlocfilehash: acf4e8df2cef3d9ec5d123a14cc7bfcd6f1bfb8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803653"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="2ced9-101">RSACng.VerifyHash nyní vrací hodnotu False pro jakékoli neúspěchy ověření</span><span class="sxs-lookup"><span data-stu-id="2ced9-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2ced9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2ced9-102">Details</span></span>|<span data-ttu-id="2ced9-103">Od verze rozhraní .NET Framework 4.6.2, vrátí tato metoda <strong>False</strong> Pokud samotný podpis má chybný formát.</span><span class="sxs-lookup"><span data-stu-id="2ced9-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="2ced9-104">Nyní vrací hodnotu false pro všechny chyby ověření. V rozhraní .NET Framework 4.6 a 4.6.1, vyvolá metoda výjimku <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> Pokud samotný podpis má chybný formát.</span><span class="sxs-lookup"><span data-stu-id="2ced9-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="2ced9-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="2ced9-105">Suggestion</span></span>|<span data-ttu-id="2ced9-106">Jakýkoli kód, jejichž spuštění závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> by se měl spustit místo toho, pokud ověření selže a metoda vrátí <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="2ced9-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="2ced9-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2ced9-107">Scope</span></span>|<span data-ttu-id="2ced9-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2ced9-108">Minor</span></span>|
|<span data-ttu-id="2ced9-109">Version</span><span class="sxs-lookup"><span data-stu-id="2ced9-109">Version</span></span>|<span data-ttu-id="2ced9-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2ced9-110">4.6.2</span></span>|
|<span data-ttu-id="2ced9-111">Type</span><span class="sxs-lookup"><span data-stu-id="2ced9-111">Type</span></span>|<span data-ttu-id="2ced9-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2ced9-112">Runtime</span></span>|
|<span data-ttu-id="2ced9-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2ced9-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
