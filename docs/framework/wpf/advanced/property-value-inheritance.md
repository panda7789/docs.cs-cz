---
title: Dědičnost hodnoty vlastnosti
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: 6af356d1c6325714fbc98cd5fe8c3ebc1825fcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547391"
---
# <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Dědičnost hodnota vlastnosti je funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systému. Dědičnost vlastnosti hodnota umožňuje podřízené elementy ve stromu elementů získat hodnotu konkrétní vlastnosti z nadřazené elementy, dědění tuto hodnotu, protože byl nastaven kdekoli v nejbližší nadřazený element. Nadřazený element může také mít získat jeho hodnota prostřednictvím dědičnost hodnotu vlastnosti, tak systému potenciálně recurses úplně do kořenového adresáře stránky. Dědičnost hodnota vlastnosti není výchozí chování systému vlastnosti; Vlastnost je nutné vytvořit s nastavením konkrétní metadata, aby způsobit, že vlastnost zahájíte dědičnost hodnotu vlastnosti na podřízené elementy.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dědičnost hodnota vlastnosti je členství ve skupině dědičnosti  
 "Dědičnosti" jako termín zde není poměrně stejný koncept jako dědičnosti v kontextu typy a obecné objektově orientované programování, kde odvozené třídy dědí člen definice jejich základních tříd. Význam dědičnosti je také v aktivní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: vlastnosti definované v různých základní třídy jsou zveřejněné jako atributy pro odvozený [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] třídy při použít jako elementy a viditelné jako členy pro kód. Dědičnost hodnota vlastnosti je zvláště o tom, jak hodnoty vlastnosti může dědit vlastnosti z jeden element do jiné na základě nadřazený podřízený vztahy v rámci stromu elementů. Stromové struktuře elementů je přímo viditelná při vnoření elementy uvnitř další prvky, jak definovat aplikace v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek. Podstromy objektů můžete také vytvořit prostřednictvím kódu programu přidáním objektů do určené kolekce jiných objektů a dědičnost hodnotu vlastnosti funguje stejným způsobem jako ve stromové struktuře dokončení za běhu.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Použití v praxi hodnota dědičnosti vlastností  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Zahrnují několik vlastností, které mají vlastnost dědičnost povolena. Tento scénář pro tyto je obvykle představují vlastnost kdy je vhodné vlastnost lze nastavit pouze jednou na stránce, že tam, kde je také členem jedné třídy base element tuto vlastnost a proto by existovat taky na většinu podřízených elementů. Například <xref:System.Windows.FrameworkElement.FlowDirection%2A> ovládacích prvků vlastnost směru plynoucích obsah by měl být uvedené a uspořádané na stránce. Obvykle je vhodné koncept toku textu zpracovávat konzistentní v rámci všech podřízených elementů. Pokud z nějakého důvodu resetování uživatelem nebo prostředí akce v určité úrovně stromu element byly směr toku, má obvykle resetovat v průběhu. Když <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost Přišla žádost o dědění, hodnota musí být pouze nastavit nebo obnovit jednou na úrovni v elementu stromové struktury, která zahrnuje prezentace potřebám každé stránce v aplikaci. Tímto způsobem zdědí i počáteční výchozí hodnota. Vlastnost modelu hodnotu dědičnosti stále umožňuje jednotlivé elementy resetovat hodnota výjimečných případech, kdy má směs směry toku je záměrné.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Provedení zděditelné vlastní vlastnosti  
 Změnou metadata vlastní vlastnosti můžete provést také vlastních vlastností zděditelné. Upozorňujeme však, určení vlastnost jako zděditelné splnit některé důležité informace o výkonu. V případech, kdy tuto vlastnost nemá zavedené místní hodnota nebo hodnota získané prostřednictvím stylů, šablony nebo datová vazba poskytuje zděditelné vlastnost jeho hodnoty přiřazené vlastností pro všechny podřízené elementy v logickém stromu.  
  
 Chcete-li vlastnost účastnit hodnota dědičnost, vytvořte vlastní přidružená vlastnost, jak je popsáno v [zaregistrovat ve vlastnosti připojené](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md). Zaregistrovat vlastnost s metadaty (<xref:System.Windows.FrameworkPropertyMetadata>) a vyberte možnost "Inherits" v nastavení možnosti v rámci této metadat. Ujistěte se také, že vlastnost má zavedené výchozí hodnotu, protože tato hodnota bude nyní dědit. I když jste zaregistrovali vlastnost jako připojen, můžete také chtít vytvořit vlastnost "obálku" pro získání nebo nastavení přístupu na vlastníka typu, stejně jako pro vlastnost "samostatný" závislosti. Až to uděláte, lze vlastnost zděditelné buď nastavit pomocí obálku přímé vlastnosti na typ vlastníka nebo odvozené typy nebo je můžete nastavit pomocí syntaxe přidružená vlastnost na žádném <xref:System.Windows.DependencyObject>.  
  
 Přidružené vlastnosti se koncepčně podobá globální vlastnosti; můžete zkontrolovat pro hodnotu na žádném <xref:System.Windows.DependencyObject> a získat platný výsledek. Typický scénář pro přidružené vlastnosti je nastavit hodnoty vlastností pro podřízené elementy a tento scénář je efektivnější, pokud je vlastnost dotyčném přidružená vlastnost, která je vždy k dispozici implicitně jako přidružená vlastnost pro každý element (<xref:System.Windows.DependencyObject>) ve stromové struktuře.  
  
> [!NOTE]
>  I když dědičnost hodnotu vlastnosti se může zdát pracovních pro vlastnosti samostatný závislostí, chování dědičnosti samostatný vlastnosti prostřednictvím určité hranice elementů ve stromové struktuře běhu není definován. Vždy používat <xref:System.Windows.DependencyProperty.RegisterAttached%2A> k registraci vlastností, kde můžete určit <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> v metadatech.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Hodnoty vlastností, která dědí napříč hranicemi stromu  
 Dědičnost vlastnosti funguje tak, že procházení stromu elementů. Tento strom je často paralelní k logickém stromu. Vždy, když však zahrnete objekt na úrovni základní grafického subsystému WPF v kód, který definuje k element stromu, jako například <xref:System.Windows.Media.Brush>, jste vytvořili nespojitým logickém stromu. Hodnota true, logického stromu neprodlužuje koncepčně prostřednictvím <xref:System.Windows.Media.Brush>, protože je koncept úrovni rozhraní WPF, logickém stromu. To se projeví ve výsledcích při použití metody uvidíte <xref:System.Windows.LogicalTreeHelper>. Však dědičnost hodnotu vlastnosti dokáže Přemostit tato mezera v logickém stromu a stále zděděné hodnoty předat prostřednictvím, tak dlouho, dokud vlastnost zděditelné byl zaregistrován jako přidružená vlastnost a žádné úmyslné blokování dědičnosti hranic (například <xref:System.Windows.Controls.Frame>) je došlo.  
  
## <a name="see-also"></a>Viz také  
 [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Přehled přidružených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Priorita hodnot vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)
