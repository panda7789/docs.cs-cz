---
ms.openlocfilehash: f70452cbadc8927521f0fcfda693586c277e4d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041148"
---
> [!CAUTION]
> Zabezpečení přístupu kódu a částečně důvěryhodný kód
>
> Rozhraní .NET Framework poskytuje mechanismus pro vynucení různých úrovní důvěryhodnosti pro různý kód spuštěný ve stejné aplikaci, který se označuje jako zabezpečení přístupu kódu (CAS).  Zabezpečení přístupu kódu v rozhraní .NET Framework by se nemělo používat jako mechanismus pro vynucení hranic zabezpečení na základě původu kódu nebo jiného aspektu identity. Naše doprovodné materiály aktualizujeme tak, aby odrážely skutečnost, že zabezpečení přístupu kódu a kód transparentní z hlediska zabezpečení se nebudou podporovat jako hranice zabezpečení s částečně důvěryhodným kódem, zejména s kódem neznámého původu. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.
>
> Tyto zásady se vztahují na všechny verze rozhraní .NET Framework, ale nevztahují se na rozhraní .NET, které je součástí Silverlightu.
