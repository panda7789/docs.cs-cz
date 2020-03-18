---
title: Bezpečné kódování pro rozhraní .NET
description: Návrhový kód pro práci s . NET vynucená oprávnění a další vynucení, které pomáhají zabránit škodlivému kódu v přístupu k datům nebo provádění jiných akcí.
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
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187731"
---
# <a name="secure-coding-guidelines"></a>Bezpečné kódování pokyny

Zabezpečení založené na důkazech a zabezpečení přístupu kódu poskytují velmi výkonné, explicitní mechanismy pro implementaci zabezpečení. Většina kódu aplikace můžete jednoduše použít infrastrukturu implementovanou rozhraním .NET. V některých případech je vyžadováno další zabezpečení specifické pro aplikaci, vytvořené rozšířením systému zabezpečení nebo pomocí nových metod ad hoc.

Pomocí .NET vynucená oprávnění a další vynucení ve vašem kódu, měli byste vytvořit bariéry zabránit škodlivý kód z přístupu k informacím, které nechcete, aby měl nebo provádět jiné nežádoucí akce. Kromě toho je nutné najít rovnováhu mezi zabezpečení a použitelnosti ve všech očekávaných scénářích pomocí důvěryhodného kódu.

Tento přehled popisuje různé způsoby, jak kód může být navržen pro práci se systémem zabezpečení.

## <a name="securing-resource-access"></a>Zabezpečení přístupu k prostředkům

Při navrhování a psaní kódu je třeba chránit a omezit přístup, který má kód k prostředkům, zejména při použití nebo vyvolání kódu neznámého původu. Takže mějte na paměti následující techniky, abyste zajistili, že váš kód je bezpečný:

- Nepoužívejte zabezpečení přístupu kódu (CAS).

- Nepoužívejte částečný důvěryhodný kód.

- Nepoužívejte atribut [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Nepoužívejte vzdálené komunikace .NET.

- Nepoužívejte distribuovaný model s komponentami (DCOM).

- Nepoužívejte binární formatters.

Zabezpečení přístupu kódu a transparentní kód zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem. Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření. Alternativními bezpečnostními opatřeními jsou:

- Virtualizace

- Kontejnery aplikací

- Uživatelé operačního systému (OS) a oprávnění

- Hyper-V kontejnery

## <a name="security-neutral-code"></a>Neutrální kód zabezpečení

Bezpečnostní neutrální kód neprovádí nic explicitního se systémem zabezpečení. Běží s bez ohledu na oprávnění, která obdrží. Přestože aplikace, kterým se nepodaří zachytit výjimky zabezpečení spojené s chráněnými operacemi (například pomocí souborů, sítí a tak dále), mohou mít za následek neošetřenou výjimku, neutrální kód zabezpečení stále využívá technologie zabezpečení v rozhraní .NET .

Neutrální knihovna se zabezpečením má zvláštní vlastnosti, kterým byste měli rozumět. Předpokládejme, že vaše knihovna poskytuje prvky rozhraní API, které používají soubory nebo volají nespravovaný kód. Pokud váš kód nemá odpovídající oprávnění, nespustí se podle popisu. Však i v případě, že kód má oprávnění, jakýkoli kód aplikace, který jej volá, musí mít stejné oprávnění, aby mohl pracovat. Pokud volající kód nemá správná oprávnění, <xref:System.Security.SecurityException> zobrazí se v důsledku procházení zásobníku zabezpečení přístupu kódu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Kód aplikace, který není opakovaně použitelnou součástí

Pokud je váš kód součástí aplikace, která nebude volána jiným kódem, zabezpečení je jednoduché a speciální kódování nemusí být vyžadováno. Nezapomeňte však, že škodlivý kód může volat váš kód. Zatímco zabezpečení přístupu kódu může zastavit škodlivý kód v přístupu k prostředkům, takový kód může stále číst hodnoty polí nebo vlastností, které mohou obsahovat citlivé informace.

Navíc pokud váš kód přijímá vstup uživatele z Internetu nebo jiných nespolehlivých zdrojů, musíte být opatrní škodlivý vstup.

## <a name="managed-wrapper-to-native-code-implementation"></a>Spravovaná obálka implementace nativního kódu

Obvykle v tomto scénáři některé užitečné funkce je implementována v nativním kódu, který chcete zpřístupnit spravovaného kódu. Spravované obálky jsou snadno psát pomocí platformy invoke nebo COM interop. Pokud to však uděláte, volající obálky musí mít nespravovaná práva kódu, aby bylo možné uspět. Podle výchozích zásad to znamená, že kód stažený z intranetu nebo Internetu nebude fungovat s obálkami.

Místo toho, aby nespravovaný kód práva pro všechny aplikace, které používají tyto obálky, je lepší dát tato práva pouze na obálku kód. Pokud základní funkce nezveřejňuje žádné prostředky a implementace je také bezpečné, obálka potřebuje pouze uplatnit svá práva, která umožňuje jakýkoli kód pro volání prostřednictvím. Pokud jsou zapojeny prostředky, kódování zabezpečení by měla být stejná jako případ kódu knihovny popsané v další části. Vzhledem k tomu, že obálka potenciálně vystavuje volající těmto prostředkům, je nutné pečlivé ověření bezpečnosti nativního kódu a je odpovědností obálky.

## <a name="library-code-that-exposes-protected-resources"></a>Kód knihovny, který zpřístupňuje chráněné prostředky

Následující přístup je nejsilnější a proto potenciálně nebezpečné (pokud se provádí nesprávně) pro kódování zabezpečení: knihovna slouží jako rozhraní pro jiný kód pro přístup k určité prostředky, které nejsou jinak k dispozici, stejně jako třídy .NET vynutit oprávnění pro prostředky, které používají. Všude tam, kde zpřístupníte prostředek, musí váš kód nejprve požadovat oprávnění odpovídající prostředku (to znamená, že musí provést kontrolu zabezpečení) a pak obvykle uplatnit svá práva k provedení skutečné operace.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Zabezpečení stavových dat](securing-state-data.md)|Popisuje, jak chránit soukromé členy.|
|[Zabezpečení a uživatelský vstup](security-and-user-input.md)|Popisuje problémy se zabezpečením aplikací, které přijímají vstup uživatele.|
|[Zabezpečení a konflikty časování](security-and-race-conditions.md)|Popisuje, jak se vyhnout sporech v kódu.|
|[Zabezpečení a průběžné vytváření kódu](security-and-on-the-fly-code-generation.md)|Popisuje problémy se zabezpečením aplikací, které generují dynamický kód.|
|[Zabezpečení na základě rolí](role-based-security.md)|Podrobně popisuje zabezpečení založené na rolích rozhraní .NET a poskytuje pokyny pro jeho použití v kódu.|
