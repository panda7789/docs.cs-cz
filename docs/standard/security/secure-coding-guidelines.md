---
title: Pokyny zabezpečení pro .NET
ms.date: 06/28/2018
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018642"
---
# <a name="secure-coding-guidelines"></a>Zabezpečené kódování zásady

Zabezpečení na základě důkazy a zabezpečení přístupu kódu poskytují velmi účinné, explicitní mechanismy zabezpečení. Většina kódu aplikace můžete jednoduše použít infrastrukturu implementovaných rozhraní .NET. V některých případech je další specifické pro aplikaci zabezpečení vyžaduje, vytvořené pomocí rozšíření systému zabezpečení nebo s použitím nové metody ad hoc.

Pomocí rozhraní .NET vynutit oprávnění a dalších vynucení ve vašem kódu, by měl postavit překážek, abyste zabránili v přístupu k informacím, že nechcete, aby měl a provádění dalších nežádoucích akcí škodlivý kód. Kromě toho musí hledají rovnováhu mezi zabezpečení a možnosti využití ve všech scénářích očekávané pomocí důvěryhodného kódu.

Tento přehled popisuje různé způsoby, jakými kódu může být navrženy pro práci s zabezpečení systému.

## <a name="securing-resource-access"></a>Zabezpečení přístupu k prostředkům

Při navrhování a psaní kódu, musíte k ochraně a omezení přístupu k prostředkům, zejména v případě použití nebo vyvoláním kódem neznámého původu. Ano mějte na paměti následující postupy k zajištění, že je váš kód zabezpečení:

- Nepoužívejte zabezpečení přístupu kódu (CAS).

- Nepoužívejte částečně důvěryhodným kódem.

- Nepoužívejte [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) atribut (APTCA).

- Nepoužívejte vzdálené komunikace .NET.

- Nepoužívejte objektu modelu DCOM (Distributed Component).

- Nepoužívejte binární formátovací moduly.

Zabezpečení přístupu kódu a kód transparentní pro zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření. Alternativní bezpečnostní opatření jsou:

- Virtualizace

- AppContainers

- Operační systém (OS) uživatelů a oprávnění

- Kontejnery Hyper-V

## <a name="security-neutral-code"></a>Neutrální kód zabezpečení

Neutrální kód zabezpečení nemá žádný účinek explicitní pomocí zabezpečení systému. Je spuštěná s oprávnění ji přijímá. I když se aplikace, které se nepodařilo zachytit výjimky zabezpečení přidružené k chráněné operací (například pomocí souborů, sítě a tak dále) může vést k neošetřené výjimce, neutrální kód zabezpečení stále využívá výhod technologií zabezpečení v rozhraní .NET .

Knihovnu zabezpečení jazykově neutrální má speciální vlastnosti, které byste měli rozumět. Předpokládejme, že vaše knihovna obsahuje prvky rozhraní API, které používají soubory nebo volání nespravovaného kódu. Pokud váš kód nemá odpovídající oprávnění, nebude fungovat, jak je popsáno. Ale i v případě, že kód má oprávnění, musí mít nějaký kód aplikace, která ho zavolá stejné oprávnění, aby bylo možné pracovat. Pokud volající kód nemá správná oprávnění <xref:System.Security.SecurityException> se zobrazí jako výsledek procházení zásobníku zabezpečení přístupu kódu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Aplikační kód, který není opětovně použitelnou komponentu

Pokud váš kód je součástí aplikace, která nesmí být volán jiným kódem, zabezpečení je jednoduché a speciální kódování nemusí být nutná. Nezapomeňte však, že škodlivý kód může volat váš kód. Při zabezpečení přístupu kódu může přestat škodlivý kód přístup k prostředkům, takový kód může i nadále načítat hodnoty pole nebo vlastnosti, které můžou obsahovat citlivé informace.

Kromě toho pokud váš kód přijímá vstup uživatele z Internetu nebo jiných nedůvěryhodných zdrojů, musíte být opatrní při škodlivý vstup.

## <a name="managed-wrapper-to-native-code-implementation"></a>Spravovaná obálka pro implementaci nativního kódu

V tomto scénáři, obvykle několik užitečných funkcí je implementované v nativním kódu, který chcete zpřístupnit pro spravovaný kód. Jednodušší zápis pomocí obou nespravovaného kódu nebo komunikace s objekty COM jsou spravované obálky. Ale pokud to uděláte, volající vašeho obálky musí mít práva nespravovaného kódu, aby bylo možné úspěšné. Podle výchozích zásad to znamená, že kód stažený z intranetu nebo Internetu nebude fungovat s obálkami.

Namísto udělení práv nespravovaný kód pro všechny aplikace, které používají tyto obálky, je lepší udělit tato oprávnění pouze kód obálky. Pokud základní funkce nezveřejňuje žádné prostředky a provedení podobně je bezpečné, obálku potřebuje pouze k vyhodnocení její práva, umožňující jakýkoli kód volání prostřednictvím. Při prostředky souvisejí, psaní kódu zabezpečení, by to být stejný jako v případě kódu knihovny je popsáno v další části. Protože obálka potenciálně vystavuje volající k těmto prostředkům, pozor, ověření bezpečnosti nativního kódu je nutné a zodpovídá za obálku.

## <a name="library-code-that-exposes-protected-resources"></a>Kód knihovny vystavující chráněné zdroje

Následující postup je nejvýkonnější a proto potenciálně nebezpečné (Pokud nesprávně) pro zabezpečení kódování: Knihovna jako rozhraní pro další kód pro přístup k určitým prostředkům, které nejsou k dispozici, jinak stejně jako třídy rozhraní .NET vynucení oprávnění pro prostředky, které používají. Bez ohledu na to zpřístupníte prostředek kódu musí nejprve vyžadují oprávnění k prostředku (to znamená, musí provést kontrolu zabezpečení) a obvykle vyhodnocení jeho práva k provedení aktuální operace.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Zabezpečení stavových dat](securing-state-data.md)|Popisuje, jak chránit soukromé členy.|
|[Zabezpečení a uživatelský vstup](security-and-user-input.md)|Popisuje aspekty zabezpečení pro aplikace, které přijímají uživatelský vstup.|
|[Zabezpečení a konflikty časování](security-and-race-conditions.md)|Popisuje, jak se vyhnout časování ve vašem kódu.|
|[Zabezpečení a průběžné vytváření kódu](security-and-on-the-fly-code-generation.md)|Popisuje aspekty zabezpečení pro aplikace, které generují dynamický kód.|
|[Zabezpečení na základě rolí](role-based-security.md)|Zabezpečení na základě role .NET podrobně popisuje a obsahuje pokyny pro použití ve vašem kódu.|
