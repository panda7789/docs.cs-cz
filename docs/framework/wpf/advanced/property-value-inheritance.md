---
title: Dědičnost hodnoty vlastnosti
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: eb757d039437d9954a2b648c5f758dffa3fee3d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958365"
---
# <a name="property-value-inheritance"></a>Dědičnost hodnoty vlastnosti
Dědičnost hodnot vlastností je funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému vlastností. Dědičnost hodnot vlastností povoluje podřízeným elementům ve stromové struktuře prvků pro získání hodnoty konkrétní vlastnosti z nadřazených prvků, která tuto hodnotu zdědí, protože byla nastavena kdekoli v nejbližším nadřazeném elementu. Nadřazený element může také získat jeho hodnotu prostřednictvím dědičnosti hodnoty vlastnosti, takže systém může přecházet všechny možnosti na kořen stránky. Dědičnost hodnoty vlastnosti není výchozím chováním systému vlastností; vlastnost musí být vytvořena s konkrétním nastavením metadat, aby mohla tato vlastnost iniciovat dědění hodnoty vlastností u podřízených elementů.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dědičnost hodnoty vlastnosti se dědičností zahrnutí.  
 "Dědičnost" jako člen není poměrně stejný koncept jako dědičnost v kontextu typů a obecného objektově orientovaného programování, kde odvozené třídy dědí definice členů ze svých základních tříd. Tento význam dědičnosti je také aktivní v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: vlastnosti definované v různých základních třídách jsou zveřejněny jako atributy pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odvozené třídy při použití jako elementy a zveřejněné jako členy pro kód. Dědičnost hodnot vlastností je obzvláště o tom, jak hodnoty vlastností mohou dědit z jednoho prvku na druhý na základě vztahů nadřazenosti a podřízenosti v rámci stromu prvků. Tento strom prvků je nejvíce přímo viditelný při vnořování prvků uvnitř jiných prvků při definování aplikací v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu. Stromy objektů lze také vytvořit programově přidáním objektů do určených kolekcí jiných objektů a dědičnost hodnoty vlastností funguje stejným způsobem v dokončeném stromu v době běhu.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Praktické aplikace dědičnosti hodnot vlastností  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Rozhraní API obsahují několik vlastností, které mají povolenou dědičnost vlastností. Obvykle se jedná o scénář, který zahrnuje vlastnost, kde je vhodné, aby vlastnost byla nastavena pouze jednou pro každou stránku, ale v případě, že tato vlastnost je také členem jedné ze základních tříd prvků, a proto by také existovala u většiny podřízených prvků. Například <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost určuje, který směr toku obsahu by měl být zobrazen a uspořádán na stránce. Obvykle je vhodné zpracovat koncept toku textu konzistentně napříč všemi podřízenými prvky. Pokud byl směr toku z nějakého důvodu resetován v určité úrovni stromu elementu podle uživatele nebo prostředí, měla by být obvykle vynulována v celém. Je-li vlastnost nastavena na dědění, je nutné nastavit nebo resetovat hodnotu pouze jednou na úrovni ve stromové struktuře prvků, která zahrnuje prezentace potřeb každé stránky v aplikaci. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Tento způsob zdědí i počáteční výchozí hodnota. Model dědičnosti hodnoty vlastností stále umožňuje, aby jednotlivé prvky obnovily hodnotu ve výjimečných případech, kde je kombinace směrů toků záměrné.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Vytvoření vlastní vlastnosti dědičné  
 Změnou metadat vlastní vlastnosti můžete také dědit vlastní vlastnosti. Všimněte si ale, že při určování vlastnosti, která je dědičná, je potřeba vzít v paměti nějaký vliv. V případech, kdy tato vlastnost nemá vytvořenou lokální hodnotu nebo hodnotu získanou prostřednictvím stylů, šablon nebo datových vazeb, umožňuje dědičná vlastnost jejich přiřazené hodnoty vlastností všem podřízeným elementům v logickém stromu.  
  
 Chcete-li, aby se vlastnost účastnila dědičnosti hodnot, vytvořte vlastní připojenou vlastnost, jak je popsáno v tématu [registrace připojené vlastnosti](how-to-register-an-attached-property.md). Zaregistrujte vlastnost s metadaty (<xref:System.Windows.FrameworkPropertyMetadata>) a v nastavení možností v rámci těchto metadat zadejte možnost Inherits. Také se ujistěte, že vlastnost má vytvořenou výchozí hodnotu, protože tato hodnota bude nyní děděna. I když jste vlastnost zaregistrovali jako připojenou, možná budete chtít vytvořit vlastnost "obálku" pro přístup k typu oprávnění get/set, stejně jako u vlastnosti závislosti "Nepřipojeno". Po tomu lze dědičnou vlastnost nastavit buď pomocí obálky přímých vlastností na typu vlastníka nebo odvozených typů, nebo je lze nastavit pomocí syntaxe <xref:System.Windows.DependencyObject>připojené vlastnosti.  
  
 Připojené vlastnosti jsou koncepčně podobné globálním vlastnostem; můžete vyhledat hodnotu v jakémkoli <xref:System.Windows.DependencyObject> a získat platný výsledek. Typický scénář pro připojené vlastnosti je nastavit hodnoty vlastností u podřízených elementů a tento scénář je efektivnější, pokud je vlastnost je připojená, která je vždy implicitně přítomna jako připojená vlastnost u každého prvku (<xref:System.Windows.DependencyObject>) ve stromu.  
  
> [!NOTE]
> I když se dědičnost hodnot vlastností může zdát fungovat pro nepřipojené vlastnosti závislosti, chování dědičnosti pro nepřipojenou vlastnost prostřednictvím určitých hranic prvků v běhovém stromu není definováno. Vždy použijte <xref:System.Windows.DependencyProperty.RegisterAttached%2A> k registraci vlastností, které zadáte <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> v metadatech.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dědění hodnot vlastností napříč hranicemi stromu  
 Dědičnost vlastností funguje procházením stromu prvků. Tento strom je často rovnoběžný s logickým stromem. Kdykoli však zahrnete objekt základní úrovně WPF do značky, který definuje strom elementu, například <xref:System.Windows.Media.Brush>, jste vytvořili nesouvislý logický strom. Skutečný logický strom bez koncepčního rozšiřování prostřednictvím <xref:System.Windows.Media.Brush>, protože logický strom je koncept na úrovni architektury WPF. Můžete vidět, že se to projeví ve výsledcích při použití metod <xref:System.Windows.LogicalTreeHelper>. Dědičnost hodnot vlastností však může přenášet tuto mezeru v logickém stromu a může nadále přenášet děděné hodnoty prostřednictvím, pokud byla dědičná vlastnost registrována jako připojená vlastnost a bez záměrného blokování dědičnosti (například <xref:System.Windows.Controls.Frame>).  
  
## <a name="see-also"></a>Viz také:

- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled přidružených vlastností](attached-properties-overview.md)
- [Priorita hodnot vlastností závislosti](dependency-property-value-precedence.md)
