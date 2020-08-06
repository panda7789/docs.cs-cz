---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855660"
---
> [!CAUTION]
> <span data-ttu-id="77980-101">Zabezpečení přístupu kódu (CAS) a částečně důvěryhodný kód</span><span class="sxs-lookup"><span data-stu-id="77980-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="77980-102">Rozhraní .NET Framework poskytuje mechanismus pro vynucení různých úrovní důvěryhodnosti pro různý kód spuštěný ve stejné aplikaci, který se označuje jako zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="77980-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="77980-103">**Certifikační autority nejsou podporované v .NET Core, .NET 5 a novějších verzích. Verze CAS nejsou podporované verzemi C#, které jsou novější než 7,0.**</span><span class="sxs-lookup"><span data-stu-id="77980-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="77980-104">Certifikační autority v .NET Framework by se neměly používat jako mechanismus pro vynucování hranic zabezpečení na základě původu kódu nebo jiných aspektů identity.</span><span class="sxs-lookup"><span data-stu-id="77980-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="77980-105">CAS a kód transparentní z hlediska zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem, zejména s kódem neznámého původu.</span><span class="sxs-lookup"><span data-stu-id="77980-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="77980-106">Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="77980-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="77980-107">Tyto zásady se vztahují na všechny verze rozhraní .NET Framework, ale nevztahují se na rozhraní .NET, které je součástí Silverlightu.</span><span class="sxs-lookup"><span data-stu-id="77980-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
