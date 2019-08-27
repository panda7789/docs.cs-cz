---
ms.openlocfilehash: f70452cbadc8927521f0fcfda693586c277e4d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041148"
---
> [!CAUTION]
> <span data-ttu-id="d8fc8-101">Zabezpečení přístupu kódu a částečně důvěryhodný kód</span><span class="sxs-lookup"><span data-stu-id="d8fc8-101">Code Access Security and Partially Trusted Code</span></span>
>
> <span data-ttu-id="d8fc8-102">Rozhraní .NET Framework poskytuje mechanismus pro vynucení různých úrovní důvěryhodnosti pro různý kód spuštěný ve stejné aplikaci, který se označuje jako zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="d8fc8-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="d8fc8-103">Zabezpečení přístupu kódu v rozhraní .NET Framework by se nemělo používat jako mechanismus pro vynucení hranic zabezpečení na základě původu kódu nebo jiného aspektu identity.</span><span class="sxs-lookup"><span data-stu-id="d8fc8-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="d8fc8-104">Naše doprovodné materiály aktualizujeme tak, aby odrážely skutečnost, že zabezpečení přístupu kódu a kód transparentní z hlediska zabezpečení se nebudou podporovat jako hranice zabezpečení s částečně důvěryhodným kódem, zejména s kódem neznámého původu.</span><span class="sxs-lookup"><span data-stu-id="d8fc8-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="d8fc8-105">Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="d8fc8-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="d8fc8-106">Tyto zásady se vztahují na všechny verze rozhraní .NET Framework, ale nevztahují se na rozhraní .NET, které je součástí Silverlightu.</span><span class="sxs-lookup"><span data-stu-id="d8fc8-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
