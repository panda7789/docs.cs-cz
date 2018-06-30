---
title: Pokyny pro rozhraní .NET zabezpečení
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
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106733"
---
# <a name="secure-coding-guidelines"></a>Pokyny pro zabezpečené kódování

Zabezpečení na základě důkaz a zabezpečení přístupu kódu poskytují velmi výkonné, explicitní mechanismy pro implementaci zabezpečení. Většinu kódu aplikace můžete jednoduše používat infrastrukturu implementované rozhraní .NET. V některých případech další bezpečnostní specifické pro aplikaci je nutné, vytvořené pomocí rozšíření zabezpečení systému nebo pomocí nových ad hoc metod.

Pomocí rozhraní .NET vynucují oprávnění a dalších vynucení ve vašem kódu, by měl postavit překážek, aby se zabránilo škodlivý kód z přístup k informacím, že nechcete, aby ji tak, aby měl nebo provádět jiné nežádoucí akce. Kromě toho musí vytvořit rovnováhu mezi zabezpečením a použitelnost ve všech scénářích očekávané pomocí důvěryhodný kód.

Tento přehled popisuje různé způsoby, jakými kód může být navrženy pro práci s zabezpečení systému.

## <a name="securing-resource-access"></a>Zabezpečení přístupu k prostředkům

Při návrhu a psaní kódu, musíte k ochraně a omezit přístup ke kódu, který má k prostředkům, zejména v případě, že pomocí nebo vyvolání kódem neznámého původu. Ano mějte na paměti následující postupy k zajištění bezpečnosti kódu:

- Nepoužívejte zabezpečení přístupu kódu (CAS).

- Nepoužívejte částečně důvěryhodným kódem.

- Nepoužívejte [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) atribut (APTCA).

- Nepoužívejte .NET Remoting.

- Nepoužívejte objektu modelu DCOM (Distributed Component).

- Nepoužívejte binární formátování.

Zabezpečení přístupu kódu a kód transparentní pro zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření. Alternativní bezpečnostní opatření jsou:

- Virtualizace

- AppContainers

- Operační systém (OS) uživatele a oprávnění

- Kontejnery technologie Hyper-V

## <a name="security-neutral-code"></a>Neutrální kód zabezpečení

Neutrální kód zabezpečení neodpovídá nic explicitní systémem zabezpečení. Je spuštěna s všechna oprávnění ji obdrží. I když se aplikace, které se nepodařilo zachytit výjimky zabezpečení přidružené k chráněné operací (například s použitím souborů, sítě a tak dále) může být k neošetřené výjimce, neutrální kód zabezpečení stále využívá výhod technologiích zabezpečení v rozhraní .NET .

Knihovnu zabezpečení jazykově neutrální má speciální vlastnosti, které byste měli vědět. Předpokládejme, že vaše knihovna poskytuje rozhraní API prvky, které používají soubory nebo volat nespravovaný kód. Pokud váš kód nemá odpovídající oprávnění, nebude fungovat, jak je popsáno. Ale i v případě, že kód má oprávnění, kód aplikace, který jej volá musí mít stejné oprávnění fungování. Pokud kód volání nemá správné oprávnění, <xref:System.Security.SecurityException> se zobrazí v důsledku procházení zásobníku zabezpečení přístupu kódu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Aplikační kód, který není opakovaně použitelné součásti

Pokud váš kód je součástí aplikace, která nebude volána jiným kódem, zabezpečení je snadná a speciální kódování nemusí být požadována. Nezapomeňte však, že škodlivý kód můžete volat váš kód. Při zabezpečení přístupu kódu může přestat škodlivý kód v přístupu k prostředkům, může takový kód stále načíst hodnoty polí nebo vlastnosti, které můžou obsahovat citlivé informace.

Kromě toho pokud váš kód přijímá uživatelského vstupu z Internetu nebo jiné nespolehlivé zdroje, musíte být opatrní škodlivý vstup.

## <a name="managed-wrapper-to-native-code-implementation"></a>Spravovaná obálka pro implementaci nativního kódu

V tomto scénáři obvykle některé užitečné funkce je implementována v nativním kódu, které mají být k dispozici do spravovaného kódu. Spravované obálky se snadno zápisu pomocí vyvolání buď platformy nebo zprostředkovatel komunikace s objekty COM. Ale pokud to uděláte, volající vašich obálek musí mít práva nespravovaného kódu, aby bylo možné úspěšně. Ve výchozích zásadách to znamená, že kód stáhnout z intranetu nebo Internetu nebude fungovat se obálky.

Namísto udělení oprávnění nespravovaného kódu na všechny aplikace, které používají tyto obálky, je lepší přidělit pouze na kód obálky tato práva. Pokud základní funkce zpřístupňuje žádné prostředky a implementace je obdobně bezpečná, obálku pouze potřebuje uplatnit její práva, která umožňuje žádný kód volání prostřednictvím. Pokud se jedná o prostředky kódování zabezpečení, musí to být stejný jako v případě kódu knihovny popsané v další části. Protože obálku potenciálně vystavuje volající na tyto prostředky, je nutné pozor, ověření bezpečnosti nativního kódu a je za to obálka.

## <a name="library-code-that-exposes-protected-resources"></a>Kód knihovny vystavující chráněné zdroje

Následující postup je nejvýkonnější a proto potenciálně nebezpečný (Pokud je nesprávně provedeno) pro kódování zabezpečení: vaše knihovna slouží jako rozhraní pro jiný kód pro přístup k určitým prostředkům, které nejsou k dispozici, jinak stejně jako vynutit třídy rozhraní .NET oprávnění pro prostředky, které používají. Bez ohledu na vystavit prostředek kódu musí nejprve požádat o oprávnění k příslušnému prostředku (to znamená, musí provést kontrolu zabezpečení) a poté obvykle uplatní jeho práva k provedení aktuální operace.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Zabezpečení stavových dat](securing-state-data.md)|Popisuje, jak chránit soukromé členy.|
|[Zabezpečení a uživatelský vstup](security-and-user-input.md)|Popisuje otázky zabezpečení pro aplikace, které přijímají vstup uživatele.|
|[Zabezpečení a konflikty časování](security-and-race-conditions.md)|Popisuje, jak se vyhnout časování ve vašem kódu.|
|[Zabezpečení a průběžné vytváření kódu](security-and-on-the-fly-code-generation.md)|Popisuje otázky zabezpečení pro aplikace, které generují dynamický kód.|
|[Zabezpečení na základě rolí](role-based-security.md)|Popisuje podrobně zabezpečení na základě rolí rozhraní .NET a poskytuje pokyny pro použití v kódu.|
