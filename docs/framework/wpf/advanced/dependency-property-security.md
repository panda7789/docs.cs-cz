---
title: Zabezpečení vlastností závislosti
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186397"
---
# <a name="dependency-property-security"></a>Zabezpečení vlastností závislosti
Vlastnosti závislostí by obecně měly být považovány za veřejné vlastnosti. Povaha systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastností zabraňuje možnost i zajištění záruky o hodnotu vlastnosti závislost.  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Přístup a zabezpečení obalů a vlastností závislostí  
 Vlastnosti závislostí jsou obvykle implementovány spolu s vlastnostmi "obálky" common language runtime (CLR), které zjednodušují získávání nebo nastavování vlastnosti z instance. Ale obálky jsou opravdu jen pohodlí <xref:System.Windows.DependencyObject.GetValue%2A> metody, které implementují základní a <xref:System.Windows.DependencyObject.SetValue%2A> statické volání, které se používají při interakci s vlastnostmi závislostí. Přemýšlíte o tom jiným způsobem, vlastnosti jsou vystaveny jako běžné jazykové runtime (CLR) vlastnosti, které se stalo, že je zálohována závislost vlastnost, nikoli soukromé pole. Mechanismy zabezpečení použité na obálky nejsou paralelní chování systému vlastností a přístup k základní vlastnost i závislost. Umístění požadavku na zabezpečení obálky zabrání pouze použití metody pohodlí, ale <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>nezabrání volání nebo . Podobně umístění chráněné nebo soukromé úrovně přístupu na obálky neposkytuje žádné účinné zabezpečení.  
  
 Pokud píšete vlastní vlastnosti závislostí, měli byste <xref:System.Windows.DependencyProperty> deklarovat obálky a pole identifikátorjako veřejné členy, takže volající nedostanou zavádějící informace o skutečné úrovni přístupu této vlastnosti (z důvodu jeho úložiště je implementováno jako vlastnost závislosti).  
  
 Pro vlastní závislost vlastnost, můžete zaregistrovat vlastnost jako vlastnost závislosti jen pro čtení, a to poskytuje efektivní prostředek k zabránění <xref:System.Windows.DependencyPropertyKey> vlastnost i nastavit kdokoli, kdo nemá odkaz na pro tuto vlastnost. Další informace naleznete v [tématu Vlastnosti závislostí jen pro čtení](read-only-dependency-properties.md).  
  
> [!NOTE]
> Deklarování <xref:System.Windows.DependencyProperty> identifikátor pole soukromé není zakázáno a může být pravděpodobně použit ke snížení okamžitě vystavený obor názvů vlastní třídy, ale taková vlastnost by neměla být považována za "soukromé" ve stejném smyslu jako definice jazyka CLR (COMMON Language runtime) definovat, že úroveň přístupu, z důvodů popsaných v další části.  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>Expozice vlastností vlastností vlastností vlastností  
 Obecně není užitečné a potenciálně zavádějící deklarovat jako jakoukoli jinou úroveň přístupu <xref:System.Windows.DependencyProperty> než veřejnou. Toto nastavení úrovně přístupu pouze zabraňuje tomu, aby někdo mohl získat odkaz na instanci z deklarující třídy. Ale existuje několik aspektů systému vlastností, <xref:System.Windows.DependencyProperty> které vrátí jako prostředek identifikace konkrétní vlastnost, jak existuje na instanci třídy nebo odvozené instance <xref:System.Windows.DependencyObject.SetValue%2A> třídy a tento identifikátor je stále použitelný ve volání i v případě, že původní statický identifikátor je deklarován jako neveřejné. <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> Virtuální metody také přijímat informace o všechny existující vlastnosti závislosti, která změnila hodnotu. Kromě toho <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda vrátí identifikátory pro všechny vlastnosti na instance s místně nastavenou hodnotou.  
  
### <a name="validation-and-security"></a>Ověření a zabezpečení  
 Použití požadavku a <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> očekává selhání ověření na selhání požadavku zabránit nastavení vlastnosti není odpovídající mechanismus zabezpečení. Zneplatnění nastavené <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> hodnoty vynucené také prostřednictvím může být také potlačeno škodlivými volajícími, pokud tito volající pracují v doméně aplikace.  
  
## <a name="see-also"></a>Viz také

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
