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
ms.openlocfilehash: 825b2a3dc79300f0cc26514398b8de0abee64fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-property-security"></a>Zabezpečení vlastností závislosti
Vlastnosti závislosti by měl být obecně považuje za veřejné vlastnosti. Povaha [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systému brání schopnost provádět záruky zabezpečení o hodnotu vlastnosti závislosti.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Přístup a zabezpečení obálky a vlastností závislostí  
 Obvykle jsou implementované vlastnosti závislosti společně s "obálky" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti, které usnadňují získání nebo nastavení vlastnosti z instance. Ale obálky jsou ve skutečnosti jenom usnadňující metody, které implementují základní <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> statické volání, které se používají při interakci s vlastností závislostí. Myslíme ho jiným způsobem, vlastnosti jsou zveřejněné jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnosti, které mají být zálohovaný pomocí vlastnosti závislosti, a nikoli soukromé pole. Mechanismy zabezpečení u obálky není paralelní vlastnost systému chování a přístup k základní vlastnosti závislosti. Uvedení požadavek zabezpečení na obálku pouze zabrání použití metody pohodlí ale nezabrání volání <xref:System.Windows.DependencyObject.GetValue%2A> nebo <xref:System.Windows.DependencyObject.SetValue%2A>. Podobně umístění chráněný, nebo na úrovni privátní přístupu obálky neposkytuje žádné efektivní zabezpečení.  
  
 Pokud píšete vlastní vlastnosti závislosti, by měly deklarovat obálky a <xref:System.Windows.DependencyProperty> identifikátor pole jako veřejné členy, tak, aby volající není získat zavádějící informace o úroveň přístupu true této vlastnosti (z důvodu jeho se úložiště implementovaný jako vlastnost závislosti).  
  
 Pro vlastnost vlastní závislosti, můžete zaregistrovat vaše vlastnost jako vlastnost závislosti jen pro čtení, a to poskytuje účinný prostředek brání nastaveno libovolný uživatel, který nemá odkaz na vlastnost <xref:System.Windows.DependencyPropertyKey> pro tuto vlastnost. Další informace najdete v tématu [jen pro čtení vlastností závislostí](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Deklarace <xref:System.Windows.DependencyProperty> soukromé pole identifikátor není zakázáno a lze případně také použít snížit okamžitě zveřejněné obor názvů vlastní třídy, ale tato vlastnost by se neměla považovat za "privátní" stejně jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyk definic definovat tuto úroveň přístupu, z důvodů, které jsou popsané v další části.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Ohrožení systému vlastností vlastností závislostí  
 Není obecně užitečné a je potenciálně zavádějící, deklarovat <xref:System.Windows.DependencyProperty> jako jakýkoli přístup na úrovni jiné než veřejné. Toto nastavení úrovně přístupu zabrání pouze někdo nebudou moct získat odkaz na instanci ze deklarující třídy. Ale existuje několik aspektů vlastnosti systému, který vrátí <xref:System.Windows.DependencyProperty> jako způsob identifikace určité vlastnosti, protože existuje v instanci třídy nebo instance odvozené třídy a tento identifikátor je stále možné použít v <xref:System.Windows.DependencyObject.SetValue%2A> i volání Pokud původní statické identifikátor je deklarován jako nonpublic. Navíc <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> virtuální metody získat informace, všechny existující vlastnosti závislosti, která změnit hodnotu. Kromě toho <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda vrátí identifikátory pro všechny vlastnosti v instancích s místně nastavte hodnotu.  
  
### <a name="validation-and-security"></a>Ověření a zabezpečení  
 Použití požadavku na <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> a byla očekávána chybu ověřování na požádání selhání zabránit se nastavuje vlastnost není mechanismus odpovídající zabezpečení. Nastavte hodnotu zneplatnění vynucují prostřednictvím <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> může také potlačit škodlivých volajících, pokud jsou tyto volající provozu v rámci domény aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
