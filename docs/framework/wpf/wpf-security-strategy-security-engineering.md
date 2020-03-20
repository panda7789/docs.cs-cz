---
title: Bezpečnostní strategie a inženýrství
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174560"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategie zabezpečení WPF – engineering zabezpečení
Trusted Computing je iniciativa společnosti Microsoft pro zajištění výroby zabezpečeného kódu. Klíčovým prvkem iniciativy Trusted Computing je životní cyklus vývoje zabezpečení společnosti Microsoft (SDL). SDL je inženýrská praxe, která se používá ve spojení se standardními inženýrskými procesy pro usnadnění dodávky zabezpečeného kódu. SDL se skládá z deseti fází, které kombinují osvědčené postupy s formalizací, měřitelností a další strukturou, včetně:  
  
- Analýza návrhu zabezpečení  
  
- Kontroly kvality založené na nástrojích  
  
- Testování průniku  
  
- Závěrečná kontrola bezpečnosti  
  
- Správa zabezpečení produktu po vydání  
  
## <a name="wpf-specifics"></a>Specifika WPF  
 Technický [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tým jak platí a rozšiřuje SDL, kombinace, která zahrnuje následující klíčové aspekty:  
  
 [Modelování hrozeb](#threat_modeling)  
  
 [Nástroje pro analýzu a úpravy zabezpečení](#tools)  
  
 [Testovací techniky](#techniques)  
  
 [Kritická správa kódu](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a>Modelování hrozeb  
 Modelování hrozeb je základní součástí SDL a slouží k profilování systému k určení potenciálních chyb zabezpečení. Jakmile jsou identifikovány chyby zabezpečení, modelování hrozeb také zajišťuje, že jsou zavedena vhodná skutečnosti snižující závažnost rizika.  
  
 Na vysoké úrovni modelování hrozeb zahrnuje následující klíčové kroky pomocí obchodu s potravinami jako příklad:  
  
1. **Identifikace majetku**. Majetek obchodu s potravinami může zahrnovat zaměstnance, trezor, pokladny a inventář.  
  
2. **Výčet vstupních bodů**. Vstupní body obchodu s potravinami mohou zahrnovat přední a zadní dveře, okna, nakládací rampu a klimatizační jednotky.  
  
3. **Vyšetřování útoků proti majetku pomocí vstupních bodů**. Jeden možný útok by se mohl zaměřit na *bezpečné* aktivum obchodu s potravinami prostřednictvím vstupního bodu *klimatizace;* klimatizační jednotka může být odšroubována, aby bylo možné trezor vytáhnout přes něj a ven z obchodu.  
  
 Modelování hrozeb [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] se používá v celém textu a zahrnuje následující:  
  
- Jak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analyzátor čte soubory, mapuje text na odpovídající třídy objektových modelů a vytváří skutečný kód.  
  
- Jak je vytvořen popisovač okna (hWnd), odesílá zprávy a používá se pro vykreslování obsahu okna.  
  
- Jak datové vazby získává prostředky a spolupracuje se systémem.  
  
 Tyto modely hrozeb jsou důležité pro identifikaci požadavků na návrh zabezpečení a zmírnění hrozeb během procesu vývoje.  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a>Nástroje pro analýzu a úpravy zdrojů  
 Kromě prvků ruční kontroly kódu zabezpečení SDL [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tým používá několik nástrojů pro analýzu zdroje a přidružené úpravy ke snížení slabá místa zabezpečení. Používá se široká škála zdrojových nástrojů, které zahrnují následující:  
  
- **FXCop**: Vyhledá běžné problémy se zabezpečením ve spravovaném kódu, od pravidel dědičnosti až po použití zabezpečení přístupu kódu až po bezpečné propojení s nespravovaným kódem. Viz [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefix/Prefast**: Vyhledá slabá místa zabezpečení a běžné problémy se zabezpečením v nespravovaném kódu, jako jsou přetečení vyrovnávací paměti, problémy s formátovacím řetězcem a kontrola chyb.  
  
- **Zakázaná řešení API**: Prohledá zdrojový kód k identifikaci náhodného použití `strcpy`funkcí, které jsou dobře známé tím, že způsobují problémy se zabezpečením, například . Po identifikaci jsou tyto funkce nahrazeny alternativami, které jsou bezpečnější.  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a>Testovací techniky  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]používá různé techniky testování zabezpečení, které zahrnují:  
  
- **Whitebox Testování**: Testeři zobrazit zdrojový kód a pak vytvořit testy zneužití.
  
- **Blackbox Testování**: Testeři se snaží najít zneužití zabezpečení kontrolou rozhraní API a funkce, a pak se pokusí zaútočit na produkt.  
  
- **Regressing security issues from other products**: V případě potřeby jsou testovány bezpečnostní problémy ze souvisejících produktů. Například byly identifikovány a vyzkoušeny vhodné varianty přibližně šedesáti problémů se [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]zabezpečením aplikace Internet Explorer a byly vyzkoušeny pro jejich použitelnost .  
  
- **Nástroje-založené penetrační testování prostřednictvím souboru fuzzing**: File fuzzing je využití vstupnírozsah čtečky souborů prostřednictvím různých vstupů. Jedním z [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] příkladů, kde se používá tato technika je kontrola selhání v kódu dekódování obrazu.  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a>Kritická správa kódu  
 Pro aplikace prohlížeče XAML (XBAPs) [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] vytvoří sandbox zabezpečení pomocí podpory rozhraní .NET Framework pro označování a sledování kódu kritického pro zabezpečení, který zvyšuje oprávnění (viz **Metodika kritické pro zabezpečení** v [wpf bezpečnostní strategii - zabezpečení platformy](wpf-security-strategy-platform-security.md)). Vzhledem k vysokým požadavkům na kvalitu zabezpečení kódu kritického pro zabezpečení obdrží tento kód další úroveň správy zdrojového kódu a audit zabezpečení. Přibližně 5 % až [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 10 % se skládá z kódu kritického pro zabezpečení, který je přezkoumán specializovaným revizním týmem. Zdrojový kód a proces vrácení se změnami je spravován sledováním kódu kritického pro zabezpečení a mapováním každé kritické entity (tj. metody, která obsahuje kritický kód) do stavu odhlášení. Stav odhlášení obsahuje jména jednoho nebo více recenzentů. Každé denní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sestavení porovná kritický kód s kódem v předchozích sestaveních a zkontroluje neschválené změny. Pokud inženýr upraví kritický kód bez souhlasu revizního týmu, je okamžitě identifikován a opraven. Tento proces umožňuje aplikaci a údržbu obzvláště vysoké [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] úrovně kontroly kódu izolovaného prostoru.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](security-wpf.md)
- [WPF částečné zabezpečení důvěryhodnosti](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Důvěryhodná výpočetní technika](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Zabezpečení v .NET](../../standard/security/index.md)
