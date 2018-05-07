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
ms.openlocfilehash: 48748267981e10be2a460f93b6f0d645951c09cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategie zabezpečení WPF – engineering zabezpečení
Trustworthy Computing je iniciativa Microsoft pro zajištění provozní zabezpečené kódu. Je klíčovým prvkem iniciativy Trustworthy Computing [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Engineering postupem, který se používá ve spojení s standardní technického procesu usnadňuje doručování zabezpečený kód je. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Se skládá z deset fází, které se zkombinovat osvědčené postupy s oblast, measurability a další struktura, včetně:  
  
-   Analýza zabezpečení návrhu  
  
-   Na základě nástroj kvality kontroly  
  
-   Testování průnikům  
  
-   Revize konečné zabezpečení  
  
-   Správa zabezpečení produktu release POST  
  
## <a name="wpf-specifics"></a>Specifika WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Technickému týmu, platí i rozšiřuje [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], která kombinace zahrnuje následující klíčové aspekty:  
  
 [Modelování hrozeb](#threat_modeling)  
  
 [Analýzu zabezpečení a nástroje pro úpravy](#tools)  
  
 [Testování techniky](#techniques)  
  
 [Kód kritický pro správu](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelování hrozeb  
 Modelování hrozeb je základní součástí [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]a slouží k profilu systému k určení potenciální ohrožení zabezpečení. Jakmile jsou identifikovány chyb zabezpečení, modelování hrozeb také zajistí jejich odpovídající zmírnění na místě.  
  
 Na vysoké úrovni modelování hrozeb zahrnuje následující kroky klíče pomocí supermarketu úložiště jako příklad:  
  
1.  **Identifikace prostředky**. Prostředky supermarketu úložiště může obsahovat zaměstnanci, sejfu, pokladny a inventáře.  
  
2.  **Vytváření výčtu vstupní body**. Určitého obchodu supermarketu vstupní body mohou zahrnovat dopředu a zpět dveře, windows, načítání ukotvení a klimatizace jednotky.  
  
3.  **Útoky na prostředky pomocí vstupních bodů na odstranění příčin**. Jeden možný útok může cílit supermarketu úložiště *bezpečné* asset prostřednictvím *klimatizace* vstupní bod; klimatizace jednotky může být unscrewed umožňuje bezpečné mají být vyžádány jeho prostřednictvím a z úložiště.  
  
 Modelování hrozeb platí v celé [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] a zahrnují následující:  
  
-   Jak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analyzátor přečte soubory, text se mapuje na odpovídající třídy modelu objektu a vytváří skutečný kód.  
  
-   Jak popisovač okna (hWnd) je vytvořen, odešle zprávy a slouží pro vykreslení obsahu časového období.  
  
-   Datová vazba jak získává prostředky a komunikuje s v systému.  
  
 Tyto hrozby modely jsou důležité pro požadavky na návrh identifikační zabezpečení a jejich zmírnění hrozeb během procesu vývoje.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Zdroj analýzy a nástroje pro úpravy  
 Kromě ruční bezpečnostní kód zkontrolovat prvky [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] používá několik nástrojů pro analýzu zdroje a přidružené úpravy snížení ohrožení zabezpečení. Širokou škálu source nástroje se používají a zahrnují následující:  
  
-   **FXCop**: Vyhledá běžné problémy se zabezpečením ve spravovaném kódu od pravidla dědičnosti až po použití zabezpečení přístupu kódu na tom, jak bezpečně spolupracovat s nespravovaným kódem. V tématu [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Nástroj předponu/Prefast**: formátu řetězce problémy a kontrola chyb najde ohrožení zabezpečení a běžné problémy se zabezpečením v nespravovaném kódu, jako je přetečení vyrovnávací paměti.  
  
-   **Zakázané rozhraní API**: hledání zdrojový kód k identifikaci nechtěné funkce, které jsou známé pro způsobuje problémy se zabezpečením, jako například `strcpy`. Jakmile jej rozpoznáte, tyto funkce jsou nahrazeny alternativy, které jsou lepší zabezpečení.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Testování techniky  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] používá celou řadu zabezpečení testování techniky, které zahrnují:  
  
-   **Testování Whitebox**: testery zobrazit zdrojový kód a následně vytvořit zneužití testů  
  
-   **Testování Blackbox**: testerům, sada zkuste najít zneužití zabezpečení tak, že prověří na rozhraní API a funkce a potom se pokusíte útokům produktu.  
  
-   **Návratu problémy se zabezpečením od jiných produktů**: Pokud je to vhodné, jsou testovány problémy se zabezpečením ze souvisejících produktů. Například vhodné variant přibližně šedesát problémy se zabezpečením [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] zjištění a o jejich vztahuje na [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Na základě nástroje Testování průnikům prostřednictvím Fuzzing souboru**: fuzzing souboru je využívání čtečku soubor vstupního rozsahu prostřednictvím řady různých vstupy. Jedním z příkladů v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kde se používá tato technika je zkontrolujte chyby v bitové kopii dekódování kódu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kód kritický pro správu  
 Pro [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sestavení karantény zabezpečení pomocí podpora v rozhraní .NET Framework pro označování a sledování kód kritický pro zabezpečení, která zvyšuje oprávnění (najdete v části **kritický pro zabezpečení metodika** v [WPF Strategie zabezpečení – platforma zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Kód kritický pro zabezpečení s ohledem požadavky na kvalitu vysoké zabezpečení, takový kód obdrží úroveň další zdroje, správu, řízení a zabezpečení auditu. Přibližně 5 až 10 % [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] se skládá z kód kritický pro zabezpečení, který je vyhrazený prostudovali tým zkontrolovat. Zdrojový kód a proces vrácení se změnami spravuje sledování kód kritický pro zabezpečení a mapování na jeho přihlašovací vypnout stavu každé kritické entity (tj. metoda, která obsahuje kód kritický pro). Přihlašovací vypnout stavu zahrnuje názvy jeden nebo více kontrolorů. Každé denní sestavení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porovná kód kritický pro který v předchozí sestavení zkontrolujte neschválených změny. Pokud technika upraví kód kritický pro bez schválení od prostudovali týmu, je jeho zjištění a napravení okamžitě. Tento proces umožní aplikaci a údržby zejména vysoký stupeň kontroly nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] izolovaného prostoru kódu.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../docs/framework/wpf/security-wpf.md)  
 [Částečné zabezpečení důvěryhodnosti WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategie zabezpečení WPF – zabezpečení platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Trustworthy Computing](http://www.microsoft.com/mscorp/twc/default.mspx)  
 [Modelování aplikace hrozeb](http://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [Pokyny pro zabezpečení: Rozhraní .NET Framework 2.0](http://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
