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
ms.openlocfilehash: d9dd9306980b80f7845c10e8c0ccb59f29821245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940841"
---
# <a name="dependency-property-security"></a>Zabezpečení vlastností závislosti
Vlastnosti závislosti by se obecně měly považovat za veřejné vlastnosti. Povaha [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému vlastností zabraňuje možnosti provádět záruky zabezpečení týkající se hodnoty vlastnosti závislosti.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Přístup k obálkám a vlastnostem závislosti a jejich zabezpečení  
 Vlastnosti závislostí jsou obvykle implementovány spolu s vlastnostmi "Obálka" modulu CLR (Common Language Runtime), které zjednodušují získávání nebo nastavování vlastnosti z instance. Ale obálky jsou ve skutečnosti pouze pohodlnými metodami, které implementují <xref:System.Windows.DependencyObject.SetValue%2A> základní <xref:System.Windows.DependencyObject.GetValue%2A> a statické volání, která se používají při interakci s vlastnostmi závislosti. Jejich úvahou jiným způsobem se vlastnosti zveřejňují jako vlastnosti modulu CLR (Common Language Runtime), ke kterým dochází v rámci vlastnosti závislosti, nikoli pomocí soukromého pole. Mechanismy zabezpečení použité pro obálky nezpůsobují paralelní chování systémových vlastností a přístup k základní vlastnosti závislosti. Umístěním požadavku zabezpečení na obálku zabráníte použití pohodlí, ale nezabráníte voláním <xref:System.Windows.DependencyObject.GetValue%2A> metody nebo. <xref:System.Windows.DependencyObject.SetValue%2A> Podobně umístění chráněného nebo privátního přístupu na obálky neposkytuje žádné efektivní zabezpečení.  
  
 Pokud píšete vlastní vlastnosti závislosti, měli byste deklarovat obálky a <xref:System.Windows.DependencyProperty> pole identifikátor jako veřejné členy, aby volající neobdrželi zavádějící informace o skutečné úrovni přístupu této vlastnosti (z důvodu jejich uložení implementováno jako vlastnost závislosti.  
  
 U vlastní vlastnosti závislosti můžete vlastnost zaregistrovat jako vlastnost závislosti jen pro čtení. to poskytuje efektivní způsob, jak zabránit tomu, aby se vlastnost nastavila kýmkoli, kdo nedrží odkaz na danou <xref:System.Windows.DependencyPropertyKey> vlastnost. Další informace najdete v tématu [vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md).  
  
> [!NOTE]
> Deklarace pole <xref:System.Windows.DependencyProperty> identifikátoru Private není zakázaná a dá se použít k omezení okamžitě vystaveného oboru názvů vlastní třídy, ale taková vlastnost by se neměla považovat za "soukromou" ve stejném smyslu jako společný jazyk. jazykové definice modulu runtime (CLR) definují úroveň přístupu z důvodů popsaných v následující části.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Stav expozice vlastností závislosti v systému vlastností  
 Není všeobecně užitečné a je potenciálně zavádějící, k deklaraci <xref:System.Windows.DependencyProperty> jako libovolné úrovně přístupu, která je jiná než veřejná. Toto nastavení úrovně přístupu zabrání pouze někomu, aby získal odkaz na instanci z deklarované třídy. Ale existuje několik aspektů systému vlastností, které vrátí <xref:System.Windows.DependencyProperty> jako způsob určení konkrétní vlastnosti, která existuje v instanci třídy nebo odvozené třídy instance, a tento identifikátor je stále použitelné <xref:System.Windows.DependencyObject.SetValue%2A> ve volání i Pokud je původní statický identifikátor deklarován jako NonPublic. <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> Virtuální metody také přijímají informace o jakékoli existující vlastnosti závislosti, která změnila hodnotu. Kromě toho <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda vrátí identifikátory pro jakoukoliv vlastnost u instancí s lokálně nastavenou hodnotou.  
  
### <a name="validation-and-security"></a>Ověření a zabezpečení  
 Použití požadavku na <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> a očekáváte selhání ověřování při selhání požadavku, aby se zabránilo tomu, že vlastnost není adekvátním mechanismem zabezpečení. Zrušení platnosti nastavení vyvolané pomocí <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> může být také potlačeno škodlivými volajícími, pokud jsou v doméně aplikace provozováni volající.  
  
## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
