---
title: Strategie zabezpečení WPF – engineering zabezpečení
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
ms.openlocfilehash: 6006024f29c37545ce95e579c7b93727d8c6bc67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547745"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategie zabezpečení WPF – engineering zabezpečení
Trustworthy Computing je iniciativy Microsoftu pro zajištění provozní bezpečný kód. Je klíčovým prvkem Trustworthy Computing iniciativa zaměřená [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Je technický postup, který se používá ve spojení s standardní technického procesu usnadňuje poskytování zabezpečeného kódu. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Sestává z deset fází, které kombinují osvědčené postupy s oblast, measurability a další strukturu, včetně:  
  
-   Analýza návrh zabezpečení  
  
-   Kontroly založené na nástroji kvality  
  
-   Testování průniku  
  
-   Zkontrolujte poslední zabezpečení  
  
-   Správa zabezpečení produktu release příspěvku  
  
## <a name="wpf-specifics"></a>Specifika WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Inženýrský tým se vztahuje i rozšiřuje [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], kombinaci, která obsahuje následující klíčové aspekty:  
  
 [Modelování hrozeb](#threat_modeling)  
  
 [Analýza zabezpečení a nástroje pro úpravy](#tools)  
  
 [Metody testování](#techniques)  
  
 [Správa kritického kódu](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelování hrozeb  
 Modelování ohrožení je základní součástí [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]a slouží k profilu systému k určení potenciální ohrožení zabezpečení. Po se naleznou modelování hrozeb také zajišťuje, že odpovídající zmírnění rizik jsou na místě.  
  
 Na vysoké úrovni modelování hrozeb zahrnuje následující základní kroky pomocí blízkým úložiště jako příklad:  
  
1.  **Identifikace prostředků**. Prostředky blízkým úložiště může obsahovat zaměstnanci, bezpečný, pokladny a inventáře.  
  
2.  **Vytváření výčtu vstupní body**. Vstupní body blízkým úložiště může obsahovat front a dveře back, windows, ukotvit načítání a klimatizace jednotky.  
  
3.  **Prošetření útoků, které prostředky pomocí vstupní body**. Jeden možných útoků může cílit na blízkým úložiště *bezpečné* asset prostřednictvím *klimatizace* vstupní bod; klimatizace jednotky může být unscrewed umožňující bezpečné načíst přes něj a z celkového počtu úložiště.  
  
 Modelování hrozeb se použije v rámci [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] a obsahuje následující:  
  
-   Jak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analyzátor načte soubory, text se mapuje na odpovídající objekt třídy modelu a vytvoří skutečný kód.  
  
-   Jak popisovač okna (hWnd) se vytvoří, odešle zprávy a slouží pro vykreslení obsahu okna.  
  
-   Jak datová vazba získá prostředky a interaguje s systému.  
  
 Tyto modely hrozeb jsou důležité pro požadavky na návrh identifikační zabezpečení a jejich zmírnění hrozeb během procesu vývoje.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Zdrojová analýza a nástroje pro úpravy  
 Kromě ruční bezpečnostní kód zkontrolovat prvky [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tým používá několik nástrojů pro analýzu zdroje a přidružené úpravy snížení ohrožení zabezpečení. Širokou škálu nástrojů se používají a zahrnují následující:  
  
-   **FXCop**: Vyhledá běžné problémy se zabezpečením ve spravovaném kódu od pravidla dědičnosti pro použití zabezpečení přístupu kódu na tom, jak bezpečně spolupracovat s nespravovaným kódem. Zobrazit [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
-   **Předpona/nástroje Prefast**: Zjistí ohrožení zabezpečení a běžné problémy se zabezpečením v nespravovaném kódu, jako je například přetečení vyrovnávací paměti, problémy řetězec formátu a kontroly chyb.  
  
-   **Rozhraní API zakázané**: Hledání zdrojového kódu k identifikaci nechtěné funkcí, které jsou dobře známé pro způsobuje problémy se zabezpečením, jako například `strcpy`. Jakmile jej rozpoznáte, tyto funkce jsou nahrazeny alternativy, které jsou lepší zabezpečení.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Metody testování  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] využíváte různé metody, které zahrnují testování zabezpečení:  
  
-   **Testování Whitebox**: Testeři zobrazení zdrojového kódu a začnete vytvářet testy před zneužitím  
  
-   **Testování Blackbox**: Testeři zkusit zjistit, že zneužije zabezpečení tím, že kontroluje rozhraní API a funkce a poté k útoku na produktu.  
  
-   **Problémy se zabezpečením vrátí z jiných produktů**: V případě potřeby jsou testovány problémy se zabezpečením ze souvisejících produktů. Například vhodné varianty přibližně 60 problémy se zabezpečením [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] identifikaci a pokusili pro jejich použitelnost [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Testování průniku založené na nástroji prostřednictvím souboru Fuzzing**: Soubor fuzzing je že využívání čtečku souboru se uživatelovo zadání rozsah přes celou řadu vstupů. Jedním z příkladů v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] použití této techniky je chcete zkontrolovat chyby v kódu dekódování obrázku.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Správa kritického kódu  
 Pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sestavení izolovaného prostoru zabezpečení pomocí podpory rozhraní .NET Framework pro označení a sledování zabezpečení kritického kódu, který má oprávnění (naleznete v tématu **kritické pro zabezpečení metodologie** v [WPF Strategie zabezpečení – zabezpečení platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Provádět požadavky na zabezpečení vysoké kvality při zabezpečení kritického kódu, takový kód obdrží další úroveň řízení a zabezpečení auditu správy zdroje. Přibližně 5 až 10 % [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kritické pro zabezpečení kód, který je vyhrazený tým si předtím prostudovali zkontroloval se skládá. Zdrojový kód a proces vrácení se změnami se spravuje zabezpečení kritický kód pro sledování a mapováním každou kritické entitu (například metodu, která obsahuje kritický kód) na jeho znaménko vypnuté. Znaménko vypnutý stav zahrnuje názvy nejméně jeden revidující. Každý každodenními buildy sady [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porovnává kritický kód, který v předchozí sestavení, která zkontroluje změny neschválených. Pokud pracovník změní kritického kódu bez schválení od revizí týmu, je zjistili a opravili okamžitě. Tento proces umožní aplikaci a údržby zejména vysoký stupeň kontroly nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kód izolovaného prostoru.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení](../../../docs/framework/wpf/security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)
- [Trustworthy Computing](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Modelování aplikace před internetovými útoky](https://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)
- [Pokyny pro zabezpečení: Rozhraní .NET Framework 2.0](https://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
