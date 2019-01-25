---
title: Dědičnost hodnoty vlastnosti
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: e6b16bc3fc482e0f640f8b2d083392e6f94de618
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520580"
---
# <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Dědičnost hodnoty vlastnosti je funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému vlastností. Dědičnost hodnoty vlastnosti umožňuje podřízené prvky ve stromové struktuře prvků, které mají získat hodnoty konkrétní vlastnosti od nadřízené prvky, jak je nastavit kdekoli v nejbližší nadřazený element dědí tuto hodnotu. Nadřazený element může také získali jeho hodnotu prostřednictvím dědičnost hodnoty vlastnosti, tak systému recurses potenciálně až po kořen stránky. Dědičnost hodnoty vlastnosti není výchozí chování systému vlastnosti; Vlastnost musí navázat s nastavením konkrétní metadat způsobí tuto vlastnost k zahájení dědičnost hodnoty vlastnosti na podřízené prvky.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dědičnost hodnoty vlastnosti je členství ve skupině dědičnost  
 "Dědičnost" jako termín, který tady není úplně stejný koncept jako dědičnosti v kontextu typů a obecné objektově orientované programování, kde odvozeným třídám dědit definice členů z jejich základních tříd. Význam dědičnosti je také v aktivní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: vlastnosti definované v různé základní třídy jsou vystaveny jako atributy pro odvozený [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] třídy, pokud používá jako prvky jako členů pro kód. Dědičnost hodnoty vlastnosti je zvláště o jak hodnoty vlastností může zdědit z jeden element do jiného na základě vztahů nadřazenosti a podřízenosti ve stromové struktuře prvků. Stromové struktuře prvků je přímo viditelné při vnoření elementů v rámci další prvky při definování aplikací v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek. Stromů objektů lze také vytvořit prostřednictvím kódu programu přidáním objektů do určené kolekce jiných objektů a dědičnost hodnoty vlastnosti funguje stejně jako ve stromové struktuře dokončení v době běhu.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Dědičnost hodnoty vlastnosti v praxi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Zahrnují několik vlastností, které mají povolené dědičnosti vlastností. Scénář pro tyto bývá, že zahrnují vlastnosti kdy je vhodné, že vlastnost nastavit pouze jednou na stránku, ale pokud tuto vlastnost je také členem jedné ze tříd base element a proto by existovat taky na většinu podřízených elementů. Například <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastností ovládacích prvků směru tok obsahu by mělo být uvedené a uspořádány na stránce. Obvykle je vhodné koncept toku textu konzistentně zpracovávat v celém všechny podřízené prvky. Směr toku byly z nějakého důvodu obnovení v určité úrovně stromu element uživatelem nebo akce prostředí, by měl obvykle obnovit v průběhu. Když <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost je k dědění, hodnota musí být pouze nastavit nebo obnovit jednou na úrovni ve stromu elementů, která zahrnuje potřebám prezentaci jednotlivých stránek v aplikaci. Tímto způsobem bude dědit i počáteční výchozí hodnotu. Model dědičnosti hodnotu vlastnosti stále umožňuje jednotlivým prvkům resetovat hodnotu výjimečných případech, kdy s kombinaci směry toku je úmyslné.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Vytváření vlastních vlastností odvoditelný  
 Změnou vlastní vlastnost metadat, můžete provést také vlastní vlastnosti odvoditelný. Všimněte si však, že určit vlastnosti jako odvoditelný mají některé důležité informace o výkonu. V případech, kdy tato vlastnost nemá zavedené místní hodnota nebo hodnota získaných styly, šablony a datové vazby poskytuje dědičnou vlastnost příslušné hodnoty přiřazené vlastnosti pro všechny podřízené prvky v logickém stromu.  
  
 Chcete-li vlastnost zapojují do dědičnosti hodnoty, vytvořte vlastní přidružená vlastnost, jak je popsáno v [registrace připojené vlastnosti](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md). Registrace vlastnosti s metadaty (<xref:System.Windows.FrameworkPropertyMetadata>) a vyberte možnost "Inherits" v nastavení možnosti v rámci těchto metadat. Ujistěte se také, že vlastnost má zavedené výchozí hodnotu, protože tato hodnota bude nyní dědí. I když jste zaregistrovali vlastnost jako připojená, můžete také chtít vytvořit vlastnost zabezpečenou "obálku" pro přístup get/set na typ vlastníka stejně, jako byste to udělali pro vlastnost "samostatný" závislosti. Až to uděláte, může být buď nastavena vlastnost odvoditelný pomocí obálky s přímým přístupem vlastnost v typu vlastníka nebo odvozené typy nebo ji můžete nastavit pomocí syntaxe připojené vlastnosti na žádném <xref:System.Windows.DependencyObject>.  
  
 Připojené vlastnosti jsou koncepčně podobné globální vlastnosti; můžete zkontrolovat hodnotu na všech <xref:System.Windows.DependencyObject> a získat platný výsledek. Typický scénář pro připojené vlastnosti je nastavit hodnoty vlastností v podřízené prvky a tento scénář je mnohem efektivnější, pokud je vlastnost dotyčný připojené vlastnosti, která je vždy implicitně k dispozici jako připojené vlastnosti na každý prvek (<xref:System.Windows.DependencyObject>) ve stromové struktuře.  
  
> [!NOTE]
>  I když se může zobrazit dědičnost hodnoty vlastnosti pro vlastnosti závislosti samostatný chování dědičnosti pro samostatný vlastnosti prostřednictvím určité hranice element ve stromové struktuře za běhu není definováno. Vždy používejte <xref:System.Windows.DependencyProperty.RegisterAttached%2A> zaregistrovat vlastnosti, kde můžete určit <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> v metadatech.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dědění hodnoty vlastností přes hranice stromu  
 Dědičnost vlastnosti funguje tak, že procházení stromu prvků. Tento strom je často paralelní Logická stromová struktura. Ale vždy, když obsahovat objekt základní úrovni WPF v kódu, který definuje stromu, například <xref:System.Windows.Media.Brush>, vytvoříte jednorázová logického stromu. Hodnota true logického stromu nerozšiřuje koncepčně prostřednictvím <xref:System.Windows.Media.Brush>, protože Logická stromová struktura je koncept úrovni rozhraní WPF. Zobrazí se to projeví ve výsledcích při použití metody <xref:System.Windows.LogicalTreeHelper>. Ale dědičnost hodnoty vlastnosti dokáže Přemostit překonání tohoto rozdílu v logickém stromu a předáním stále zděděné hodnoty, tak dlouho, dokud vlastnost odvoditelný byl registrován jako připojené vlastnosti a žádné úmyslné blokování dědičnosti hranic (například <xref:System.Windows.Controls.Frame>) dochází.  
  
## <a name="see-also"></a>Viz také:
- [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
- [Přehled přidružených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
- [Priorita hodnot vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)
