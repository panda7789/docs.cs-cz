---
title: Pokyny k zabezpečenému kódování pro .NET
description: Navrhněte kód pro práci s. Vynuceně vynucovat oprávnění a jiné vynucování, které pomůžou zabránit škodlivému kódu v přístupu k datům nebo provádět jiné akce.
ms.date: 07/15/2020
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555953"
---
# <a name="secure-coding-guidelines"></a>Pokyny pro zabezpečené kódování

Většina kódu aplikace může jednoduše použít infrastrukturu implementovanou rozhraním .NET. V některých případech je potřeba další zabezpečení specifické pro aplikace, které je postavené buď rozšířením systému zabezpečení, nebo pomocí nových ad hoc metod.

Pomocí vynuceného oprávnění .NET a dalšího vynucování ve vašem kódu byste měli nasazovat bariéry, aby nedocházelo ke škodlivému kódu v přístupu k informacím, které nechcete mít nebo by prováděly jiné nežádoucí akce. Navíc je nutné přeškrtnout rovnováhu mezi zabezpečením a použitelností ve všech očekávaných scénářích pomocí důvěryhodného kódu.

Tento přehled popisuje různé způsoby, jak kód může být navržen pro práci se systémem zabezpečení.

## <a name="securing-resource-access"></a>Zabezpečení přístupu k prostředkům

Při navrhování a psaní kódu musíte chránit a omezit přístup k prostředkům, zejména při použití nebo vyvolání kódu neznámého původu. Mějte proto na paměti následující postupy, abyste zajistili, že je váš kód zabezpečený:

- Nepoužívejte zabezpečení přístupu kódu (CAS).

- Nepoužívejte částečně důvěryhodný kód.

- Nepoužívejte atribut [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Nepoužívejte vzdálenou komunikaci rozhraní .NET.

- Nepoužívejte model DCOM (Distributed Component Object Model).

- Nepoužívejte binární formátovací moduly.

Zabezpečení přístupu kódu a kód transparentní z hlediska zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření. Alternativní bezpečnostní opatření:

- Virtualizace

- AppContainers

- Uživatelé a oprávnění operačního systému (OS)

- Kontejnery Hyper-V

## <a name="security-neutral-code"></a>Neutrální kód pro zabezpečení

Kód neutrální z hlediska zabezpečení nijak nedělá explicitně se systémem zabezpečení. Spouští se bez jakýchkoli oprávnění, která obdrží. Přestože aplikace, které nedokázaly zachytit výjimky zabezpečení přidružené k chráněným operacím (například použití souborů, sítě atd.), mohou způsobit neošetřenou výjimku, kód neutrální od zabezpečení stále využívá technologie zabezpečení v rozhraní .NET.

Knihovna neutrální od zabezpečení má zvláštní charakteristiky, které byste měli pochopit. Předpokládejme, že vaše knihovna poskytuje prvky rozhraní API, které používají soubory, nebo volání nespravovaného kódu. Pokud váš kód nemá odpovídající oprávnění, nebude spuštěn, jak je popsáno. Nicméně i v případě, že má kód oprávnění, musí mít jakýkoli kód aplikace, který ji volá, stejné oprávnění, aby fungoval. Pokud volající kód nemá správné oprávnění, <xref:System.Security.SecurityException> zobrazí se jako výsledek procházení zásobníku zabezpečení přístupu kódu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Kód aplikace, který není opakovaně použitelná součást

Pokud je váš kód součástí aplikace, která nebude volána jiným kódem, zabezpečení je jednoduché a speciální kódování nemusí být vyžadováno. Nezapomeňte však, že škodlivý kód může zavolat váš kód. I když zabezpečení přístupu kódu může zabránit škodlivému kódu v přístupu k prostředkům, může takový kód pořád číst hodnoty polí nebo vlastností, které mohou obsahovat citlivé informace.

Kromě toho, pokud kód akceptuje vstup uživatele z Internetu nebo jiných nespolehlivých zdrojů, musíte mít pozor na škodlivý vstup.

## <a name="managed-wrapper-to-native-code-implementation"></a>Spravovaná obálka s implementací nativního kódu

Obvykle v tomto scénáři jsou některé užitečné funkce implementovány v nativním kódu, který chcete zpřístupnit spravovanému kódu. Spravované obálky lze snadno psát pomocí volání platforem nebo zprostředkovatele komunikace s objekty COM. Nicméně pokud to uděláte, volající na vašich obálkách musí mít oprávnění nespravovaného kódu, aby bylo úspěšné. V části výchozí zásady to znamená, že kód stažený z intranetu nebo z Internetu nebude fungovat s obálkami.

Místo poskytování nespravovaných oprávnění kódu pro všechny aplikace, které používají tyto obálky, je lepší poskytnout tato práva pouze kódu obálky. Pokud základní funkce zveřejňuje žádné prostředky a implementace je také bezpečná, Obálka musí vyhodnotit její práva, což umožní jakémukoli volání prostřednictvím kódu. V případě, že se jedná o prostředky, musí být kódování zabezpečení stejné jako v případě kódu knihovny popsané v další části. Vzhledem k tomu, že obálka potenciálně vystavuje volajícím tyto prostředky, pečlivé ověření bezpečnosti nativního kódu je nezbytné a je odpovědností obálky.

## <a name="library-code-that-exposes-protected-resources"></a>Kód knihovny, který zveřejňuje chráněné prostředky

Následující přístup je nejužitečnější, tedy potenciálně nebezpečný (Pokud je to správně proveden) pro kódování zabezpečení: vaše knihovna slouží jako rozhraní pro jiný kód pro přístup k určitým prostředkům, které nejsou jinak dostupné, stejně jako třídy .NET vynutila oprávnění pro prostředky, které používají. Bez ohledu na to, jaký stav vystavíte, musí váš kód nejdřív vyžadovat oprávnění odpovídající prostředku (to znamená, že musí provést kontrolu zabezpečení) a pak obvykle vyhodnotit jeho práva k provedení skutečné operace.

## <a name="see-also"></a>Viz také

- [Zabezpečení stavových dat](securing-state-data.md)
- [Zabezpečení a uživatelský vstup](security-and-user-input.md)
- [Zabezpečení a konflikty časování](security-and-race-conditions.md)
- [Zabezpečení a průběžné vytváření kódu](security-and-on-the-fly-code-generation.md)
- [Zabezpečení na základě rolí](role-based-security.md)
- [ASP.NET Core zabezpečení](/aspnet/core/security/)
