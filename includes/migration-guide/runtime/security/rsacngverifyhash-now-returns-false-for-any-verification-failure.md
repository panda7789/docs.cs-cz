---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857573"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="70f1c-101">RSACng.VerifyHash nyní vrací hodnotu False pro jakékoli neúspěchy ověření</span><span class="sxs-lookup"><span data-stu-id="70f1c-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="70f1c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="70f1c-102">Details</span></span>|<span data-ttu-id="70f1c-103">Od verze rozhraní .NET Framework 4.6.2, vrátí tato metoda <strong>False</strong> Pokud samotný podpis má chybný formát.</span><span class="sxs-lookup"><span data-stu-id="70f1c-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="70f1c-104">Nyní vrací hodnotu false pro všechny chyby ověření. V rozhraní .NET Framework 4.6 a 4.6.1, vyvolá metoda výjimku <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> Pokud samotný podpis má chybný formát.</span><span class="sxs-lookup"><span data-stu-id="70f1c-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="70f1c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="70f1c-105">Suggestion</span></span>|<span data-ttu-id="70f1c-106">Jakýkoli kód, jejichž spuštění závisí na zpracování <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> by se měl spustit místo toho, pokud ověření selže a metoda vrátí <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="70f1c-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="70f1c-107">Scope</span><span class="sxs-lookup"><span data-stu-id="70f1c-107">Scope</span></span>|<span data-ttu-id="70f1c-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="70f1c-108">Minor</span></span>|
|<span data-ttu-id="70f1c-109">Version</span><span class="sxs-lookup"><span data-stu-id="70f1c-109">Version</span></span>|<span data-ttu-id="70f1c-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="70f1c-110">4.6.2</span></span>|
|<span data-ttu-id="70f1c-111">type</span><span class="sxs-lookup"><span data-stu-id="70f1c-111">Type</span></span>|<span data-ttu-id="70f1c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="70f1c-112">Runtime</span></span>|
|<span data-ttu-id="70f1c-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="70f1c-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

