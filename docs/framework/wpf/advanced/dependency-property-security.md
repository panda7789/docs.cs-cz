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
ms.openlocfilehash: d51f8f5fd704b0c95b8e6f841b9b0ff8567899cb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364811"
---
# <a name="dependency-property-security"></a>Zabezpečení vlastností závislosti
Vlastnosti závislosti by měla být obecně považují za veřejné vlastnosti. Povaha [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost brání nemůže provádět záruky zabezpečení o hodnotu vlastnosti závislosti.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Přístup a zabezpečení obálky a vlastnosti závislosti  
 Obvykle jsou implementované vlastnosti závislosti spolu s zabezpečenou "obálku" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti, které usnadňují získání nebo nastavení vlastnosti z instance. Ale obálkami jsou ve skutečnosti jenom vhodné metody, které implementují základní <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> statické volání, které se používají při interakci s vlastnosti závislosti. Uvažujete o ho jiným způsobem, vlastnosti jsou vystaveny jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti, ke kterým dochází pro vlastnost závislosti spíše než soukromé pole zálohování. Mechanismy zabezpečení u obálkami není paralelní vlastnost chování systému a přístup k základní vlastnost závislosti. Uvedení požadavku zabezpečení na obálku pouze brání použití metody pohodlí, ale nezabrání volání <xref:System.Windows.DependencyObject.GetValue%2A> nebo <xref:System.Windows.DependencyObject.SetValue%2A>. Podobně uvedení chráněné nebo soukromý přístup na obálkami neposkytuje žádné efektivní zabezpečení.  
  
 Pokud vytváříte vlastní vlastnosti závislosti, byste měli deklarovat obálkami a <xref:System.Windows.DependencyProperty> identifikátor pole jako veřejné členy, aby volající není získat zavádějící informace o úroveň přístupu true dané vlastnosti (z důvodu jeho úložiště se implementováno jako vlastnost závislosti).  
  
 Pro vlastnost závislosti vlastní, můžete zaregistrovat vaše vlastnost jako vlastnost závislosti jen pro čtení, a to poskytuje efektivní způsob zabránění nastavování kdokoli, který neobsahuje odkaz na vlastnost <xref:System.Windows.DependencyPropertyKey> pro tuto vlastnost. Další informace najdete v tématu [vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md).  
  
> [!NOTE]
>  Deklarace <xref:System.Windows.DependencyProperty> privátní pole identifikátor není je zakázané a lze případně snížit okamžitě vystavené obor názvů vlastní třídy, ale tato vlastnost by neměly být zahrnuté "privátní" ve stejném smyslu jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyk definice definovat úrovně přístupu, z důvodů popsaných v další části.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Vlastnost systému vystavení vlastností závislosti  
 Není obecně užitečné a je potenciálně matoucí, chcete-li deklarovat <xref:System.Windows.DependencyProperty> jako přístup na úrovni jiné než public. Toto nastavení úrovně přístupu někdo pouze zabraňuje tomu nebudou moct získat odkaz na instanci ze třídy deklarující. Ale existuje několik aspektů vlastnost systému, který vrátí <xref:System.Windows.DependencyProperty> jako způsob identifikace určité vlastnosti, jak existuje v instanci třídy nebo instance odvozené třídy, a tento identifikátor je stále možné používat ve <xref:System.Windows.DependencyObject.SetValue%2A> i volání Pokud je původní statické identifikátor deklarovaný jako nonpublic. Navíc <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> virtuální metody přijetí informací o libovolné existujícího závislosti vlastnosti, která se změnila hodnota. Kromě toho <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda vrátí identifikátory pro všechny vlastnosti v instancích místně nastavené hodnotu.  
  
### <a name="validation-and-security"></a>Ověřování a zabezpečení  
 Použití požadavku na <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> a očekává neúspěšné ověření na vyžádání selhání zabránit nastavena vlastnost není adekvátní bezpečnostní mechanismus. Nastavit hodnotu zneplatnění vynutit prostřednictvím <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> může také potlačit škodlivý volajícím, pokud tyto volajícím jsou zpracovávána v rámci domény aplikace.  
  
## <a name="see-also"></a>Viz také:
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
