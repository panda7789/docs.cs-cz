---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855660"
---
> [!CAUTION]
> Zabezpečení přístupu kódu (CAS) a částečně důvěryhodný kód
>
> Rozhraní .NET Framework poskytuje mechanismus pro vynucení různých úrovní důvěryhodnosti pro různý kód spuštěný ve stejné aplikaci, který se označuje jako zabezpečení přístupu kódu (CAS).
>
> **Certifikační autority nejsou podporované v .NET Core, .NET 5 a novějších verzích. Verze CAS nejsou podporované verzemi C#, které jsou novější než 7,0.**
>
> Certifikační autority v .NET Framework by se neměly používat jako mechanismus pro vynucování hranic zabezpečení na základě původu kódu nebo jiných aspektů identity. CAS a kód transparentní z hlediska zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem, zejména s kódem neznámého původu. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.
>
> Tyto zásady se vztahují na všechny verze rozhraní .NET Framework, ale nevztahují se na rozhraní .NET, které je součástí Silverlightu.
