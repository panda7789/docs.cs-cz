---
title: Dědičnost hodnoty vlastnosti
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: b63f307d9edffd14315d383d8e06419fa141aee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187196"
---
# <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Dědičnost hodnoty vlastnosti [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vlastností systému vlastností. Dědičnost hodnoty vlastnosti umožňuje podřízeným prvkům ve stromu prvků získat hodnotu určité vlastnosti z nadřazených prvků a dědit tuto hodnotu tak, jak byla nastavena kdekoli v nejbližším nadřazeném prvku. Nadřazený prvek může také získali jeho hodnotu prostřednictvím dědičnosti hodnoty vlastnosti, takže systém potenciálně recurses celou cestu do kořenového adresáře stránky. Dědičnost hodnoty vlastnosti není výchozí chování systému vlastností; vlastnost musí být vytvořena s nastavením konkrétní metadata, aby se toto vlastnosti iniciovat dědičnost hodnoty vlastnosti na podřízené prvky.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dědičnost hodnoty vlastnosti je dědičnost uzavření  
 "Dědičnost" jako termín zde není zcela stejný koncept jako dědičnost v kontextu typů a obecné objektově orientované programování, kde odvozené třídy dědí definice členů z jejich základní třídy. Tento význam dědičnosti je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také aktivní v : vlastnosti definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] různých základních tříd jsou vystaveny jako atributy pro odvozené třídy při použití jako prvky a vystaveny jako členy pro kód. Dědičnost hodnoty vlastnosti je zejména o tom, jak hodnoty vlastností může dědit z jednoho prvku do druhého na základě vztahů nadřazený podřízený ve stromu prvků. Tento strom prvků je nejvíce přímo viditelné při vnoření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvků uvnitř jiných prvků při definování aplikací v značek. Stromy objektů lze také vytvářet programově přidáním objektů do určených kolekcí jiných objektů a dědičnost hodnoty vlastnosti funguje stejným způsobem v dokončeném stromu za běhu.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>
## <a name="practical-applications-of-property-value-inheritance"></a>Praktické aplikace dědičnosti hodnoty nemovitosti  
 Rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API obsahují několik vlastností, které mají povolenou dědičnost vlastností. Obvykle scénář pro tyto je, že zahrnují vlastnost, kde je vhodné, aby vlastnost nastavit pouze jednou na stránku, ale pokud tato vlastnost je také členem jedné z tříd základní prvek a proto by také existovat na většině podřízených prvků. Například <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost určuje, který směr tok obsahu by měly být prezentovány a uspořádány na stránce. Obvykle chcete, aby koncept toku textu bylo zpracováno konzistentně ve všech podřízených prvcích. Pokud směr toku byly z nějakého důvodu obnovit v určité úrovni stromu prvků podle akce uživatele nebo prostředí, by měla být obvykle obnovit v celém. Když <xref:System.Windows.FrameworkElement.FlowDirection%2A> je vlastnost provedena dědit, hodnota musí být nastavena nebo resetována pouze jednou na úrovni ve stromu prvků, který zahrnuje potřeby prezentace každé stránky v aplikaci. Tímto způsobem zdědí i počáteční výchozí hodnotu. Model dědičnosti hodnoty vlastnosti stále umožňuje jednotlivým prvkům obnovit hodnotu pro vzácné případy, kdy je záměrná kombinace směrů toku.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>
## <a name="making-a-custom-property-inheritable"></a>Vytvoření vlastní vlastnosti dědičné  
 Změnou metadat vlastní vlastnosti můžete také nastavit vlastní vlastnosti dědičné. Všimněte si však, že označení vlastnosti jako dědičné má některé aspekty výkonu. V případech, kdy tato vlastnost nemá zavedenou místní hodnotu nebo hodnotu získanou prostřednictvím stylů, šablon nebo datové vazby, poskytuje dědičná vlastnost své přiřazené hodnoty vlastností všem podřízeným prvkům v logickém stromu.  
  
 Chcete-li, aby se vlastnost účastnila dědičnosti hodnoty, vytvořte vlastní připojenou vlastnost, jak je popsáno v [seznamu Registrovat připojenou vlastnost](how-to-register-an-attached-property.md). Zaregistrujte vlastnost s<xref:System.Windows.FrameworkPropertyMetadata>metadaty ( ) a zadejte volbu "Dědí" v nastavení voleb v rámci tohoto metadat. Také se ujistěte, že vlastnost má stanovenou výchozí hodnotu, protože tato hodnota bude nyní dědit. Přestože jste vlastnost zaregistrovali jako připojenou, můžete také chtít vytvořit vlastnost "obálka" pro přístup k získání nebo nastavení na typ vlastníka, stejně jako pro "nepřipojenou" vlastnost závislosti. Poté lze dědičnou vlastnost nastavit pomocí obálky přímé vlastnosti na typu vlastníka nebo odvozených typů, nebo ji lze <xref:System.Windows.DependencyObject>nastavit pomocí syntaxe připojené vlastnosti na libovolném .  
  
 Připojené vlastnosti jsou koncepčně podobné globálním vlastnostem; můžete zkontrolovat hodnotu na <xref:System.Windows.DependencyObject> libovolné a získat platný výsledek. Typický scénář pro připojené vlastnosti je nastavit hodnoty vlastností na podřízené prvky a tento scénář je účinnější, pokud je vlastnost v<xref:System.Windows.DependencyObject>otázce připojené vlastnosti, která je vždy implicitně přítomen jako připojené vlastnosti na každý prvek ( ) ve stromu.  
  
> [!NOTE]
> Přestože dědičnost hodnoty vlastnosti může vypadat jako práce pro nepřipojené vlastnosti závislostí, chování dědičnosti pro nepřipojenou vlastnost prostřednictvím určitých hranic prvků ve stromu za běhu není definováno. Vždy <xref:System.Windows.DependencyProperty.RegisterAttached%2A> používejte k registraci <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> vlastností, kde zadáte v metadatech.  
  
<a name="InheritanceContext"></a>
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dědění hodnot vlastností přes hranice stromu  
 Dědičnost vlastností funguje tak, že prochází strom prvků. Tento strom je často rovnoběžný s logickým stromem. Však vždy, když zahrnete WPF na úrovni jádra objektu <xref:System.Windows.Media.Brush>ve značkách, který definuje strom prvku, jako je například , jste vytvořili nesouvislý logický strom. Skutečný logický strom nekoncepčně <xref:System.Windows.Media.Brush>rozšiřuje prostřednictvím , protože logický strom je koncept na úrovni architektury WPF. Můžete vidět to odráží ve výsledcích při <xref:System.Windows.LogicalTreeHelper>použití metod . Dědičnost hodnoty vlastnosti však může překlenout tuto mezeru v logickém stromu a může stále předat zděděné hodnoty, pokud <xref:System.Windows.Controls.Frame>byla dědičná vlastnost registrována jako připojená vlastnost a nebyla zjištěna žádná záměrná hranice blokování dědičnosti (například ) .  
  
## <a name="see-also"></a>Viz také

- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled přidružených vlastností](attached-properties-overview.md)
- [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md)
