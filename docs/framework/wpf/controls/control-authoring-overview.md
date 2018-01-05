---
title: "Přehled řízeného vytváření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca474b4a63ed907c73306e7b7f1fb39c948f12d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="control-authoring-overview"></a>Přehled řízeného vytváření
Rozšiřitelnost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] model řízení výrazně snižuje potřebu vytvářet nový ovládací prvek. Ale v některých případech může stále potřebujete vytvořit vlastní ovládací prvek. Toto téma popisuje funkce, které minimalizovat vašim potřebám k vytvoření vlastního ovládacího prvku a jiné řízení vytváření modelů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Toto téma ukazuje, jak vytvořit nový ovládací prvek.  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Alternativy k zápisu nového ovládacího prvku  
 V minulosti Pokud chcete získat přizpůsobené prostředí z existujícího ovládacího prvku, jste omezeny na změny standardních vlastností ovládacího prvku, například barvu pozadí, šířka ohraničení a velikost písma. Pokud jste si přáli rozšířit vzhled nebo chování ovládacího prvku nad rámec těchto předdefinovaných parametrů, musíte vytvořit nový ovládací prvek, obvykle dědění z ovládacího prvku existující a přepsání metody odpovědný za vykreslení ovládacího prvku.  I když stále možnost, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vám umožňuje přizpůsobit existujících ovládacích prvků pomocí jeho bohaté modelu obsahu, styly, šablony a aktivační události. V následujícím seznamu jsou uvedeny příklady jak tyto funkce slouží k vytvoření vlastních a konzistentní prostředí bez nutnosti vytvářet nový ovládací prvek.  
  
-   **Formátovaný obsah.** Mnoho standardní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky podporují složitý obsah. Například obsahu vlastnosti <xref:System.Windows.Controls.Button> je typu <xref:System.Object>, takže teoreticky nic lze zobrazit na <xref:System.Windows.Controls.Button>.  Pokud chcete, aby tlačítko Zobrazit bitové kopie a text, můžete přidat bitovou kopii a <xref:System.Windows.Controls.TextBlock> k <xref:System.Windows.Controls.StackPanel> a přiřaďte <xref:System.Windows.Controls.StackPanel> k <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost. Protože ovládací prvky můžete zobrazit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální prvky a libovolná data méně nutné vytvořit nový ovládací prvek nebo k úpravě existujícího ovládacího prvku pro podporu komplexní vizualizace. Další informace o modelu obsahu pro <xref:System.Windows.Controls.Button> a jiný obsah modely v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [modelu obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
-   **Styly.** A <xref:System.Windows.Style> je kolekce hodnot, které představují vlastnosti pro ovládací prvek. Pomocí stylů, můžete vytvořit opakovaně použitelný reprezentaci požadované řízení vzhledu a chování bez nutnosti napsat nový ovládací prvek. Předpokládejme například, že chcete všechny vaše <xref:System.Windows.Controls.TextBlock> ovládacích prvků tak, aby měl red, Arial písma a velikost písma 14. Můžete vytvořit styl jako prostředek a nastavte příslušné vlastnosti odpovídajícím způsobem. Pak každých <xref:System.Windows.Controls.TextBlock> přidat do vaší aplikace bude mít stejný vzhled.  
  
-   **Data šablony.** A <xref:System.Windows.DataTemplate> umožňuje přizpůsobit zobrazení dat v ovládacím prvku. Například <xref:System.Windows.DataTemplate> umožňuje určit, jak se data zobrazí v <xref:System.Windows.Controls.ListBox>.  Příklad tohoto, naleznete v části [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).  Kromě přizpůsobení vzhledu dat, <xref:System.Windows.DataTemplate> může zahrnovat prvky uživatelského rozhraní, které vám přináší značnou flexibilitu v vlastní uživatelská rozhraní.  Například pomocí <xref:System.Windows.DataTemplate>, můžete vytvořit <xref:System.Windows.Controls.ComboBox> v které každá položka obsahuje zaškrtávací políčko.  
  
-   **Ovládací prvek šablony.** Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používat <xref:System.Windows.Controls.ControlTemplate> definovat strukturu a vzhled, který odděluje vzhledu ovládacího prvku z funkce ovládacího prvku ovládacího prvku. Můžete výrazně změnit vzhled ovládacího prvku opětovná definice jeho <xref:System.Windows.Controls.ControlTemplate>.  Předpokládejme například, že chcete ovládací prvek, který vypadá semafor. Tento ovládací prvek obsahuje jednoduché uživatelské rozhraní a funkce.  Ovládací prvek je tři kruhy, pouze jeden z nich může lit v čase. Po některé reflexe vám nejspíš jasné, <xref:System.Windows.Controls.RadioButton> nabízí funkce pouze jeden vybrat na dobu, ale výchozí vzhled <xref:System.Windows.Controls.RadioButton> nic zdá indikátory na semafor.  Protože <xref:System.Windows.Controls.RadioButton> používá šablonu řízení k definování její vzhled lze snadno znovu definovat <xref:System.Windows.Controls.ControlTemplate> podle požadavků ovládacího prvku a zkontrolujte vaše semafor pomocí přepínače.  
  
    > [!NOTE]
    >  I když <xref:System.Windows.Controls.RadioButton> můžete použít <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> není dostatečná v tomto příkladu.  <xref:System.Windows.DataTemplate> Definuje vzhled elementů obsah ovládacího prvku. U <xref:System.Windows.Controls.RadioButton>, je obsah, ať se zobrazí vpravo kruhu, která určuje, zda <xref:System.Windows.Controls.RadioButton> je vybrána.  V příkladu semafor přepínač musí být právě kruh, který můžete "light nahoru." Protože se tak liší od výchozí vzhled vzhled požadavek semafor <xref:System.Windows.Controls.RadioButton>, je třeba znovu definovat <xref:System.Windows.Controls.ControlTemplate>.  Obecně <xref:System.Windows.DataTemplate> slouží k definování obsah (nebo dat) z ovládacího prvku a <xref:System.Windows.Controls.ControlTemplate> slouží k definování struktury ovládacího prvku.  
  
-   **Aktivační události.** A <xref:System.Windows.Trigger> umožňuje dynamicky změnit vzhled a chování ovládacího prvku bez vytvoření nového ovládacího prvku. Předpokládejme například, máte více <xref:System.Windows.Controls.ListBox> ovládací prvky v aplikaci a chcete položky v každé <xref:System.Windows.Controls.ListBox> být tučně a červeně při je tato možnost vybrána. Vaše první instinct může být pro vytvoření třídy, která dědí z <xref:System.Windows.Controls.ListBox> a přepsat <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metoda změnit vzhled vybranou položku, ale je vhodnější je přidat do styl pro aktivační událost <xref:System.Windows.Controls.ListBoxItem> který mění vzhled vybranou položku. Aktivační událost umožňuje změnit hodnoty vlastností nebo provádět akce na základě hodnoty vlastnosti. <xref:System.Windows.EventTrigger> Umožňuje provést akce, když dojde k události.  
  
 Další informace o stylů, šablony a aktivačních událostí najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Obecně platí Pokud vlastní ovládací prvek zrcadlí funkce existujícího ovládacího prvku, ale chcete prvek vypadat jinak, nejprve zvažte zda můžete některou z metod popsaných v této části můžete změnit pomocí vzhled existující ovládacího prvku.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Modely pro vytváření ovládacího prvku  
 Bohaté modelu obsahu, styly, šablony a aktivační události minimalizovat nutnost vám umožní vytvořit nový ovládací prvek. Pokud potřebujete vytvořit nový ovládací prvek, je ale důležité si uvědomit, vytváření modelů v různých ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje tři obecné modely pro vytvoření ovládacího prvku, z nichž každý obsahuje jinou sadu funkcí a úroveň flexibilitu. Základní třídy pro tři modely jsou <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, a <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>Odvozování z UserControl  
 Nejjednodušší způsob, jak vytvořit ovládací prvek v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je odvozena ze <xref:System.Windows.Controls.UserControl>. Při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Controls.UserControl>, přidáte do existující součásti <xref:System.Windows.Controls.UserControl>, název komponenty a odkazovat na obslužné rutiny událostí v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pak můžete odkazovat pojmenované elementy a definovat obslužné rutiny událostí v kódu. Tento model vývoje je velmi podobný jako model použitý pro vývoj aplikací v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pokud je vytvořen správně, <xref:System.Windows.Controls.UserControl> můžete využít výhod bohaté obsahu, styly a aktivační události. Ale pokud vlastní ovládací prvek dědí z <xref:System.Windows.Controls.UserControl>, uživatelé, kteří používají vlastní ovládací prvek nebude možné použít <xref:System.Windows.DataTemplate> nebo <xref:System.Windows.Controls.ControlTemplate> přizpůsobit její vzhled.  Je nutné odvozovat z <xref:System.Windows.Controls.Control> třídu nebo jedna z jeho odvozených tříd (jiné než <xref:System.Windows.Controls.UserControl>) vytvořit vlastní ovládací prvek, který podporuje šablony.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>Výhody odvozování z UserControl  
 Vezměte v úvahu odvozování z <xref:System.Windows.Controls.UserControl> pokud platí všechny následující kroky:  
  
-   Chcete vytvořit řízení podobně jak sestavit aplikaci.  
  
-   Vlastní ovládací prvek se skládá jenom z existující součásti.  
  
-   Nemusíte podporovat komplexní přizpůsobení.  
  
### <a name="deriving-from-control"></a>Odvozování z ovládacího prvku  
 Odvozování z <xref:System.Windows.Controls.Control> třída je model používá většina existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky. Při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Controls.Control> třídu, zadejte její vzhled pomocí šablon. Díky tomu oddělit provozní logiku z vizuální reprezentace. Můžete také zajistit oddělení uživatelského rozhraní a logiku pomocí příkazů a vazby místo události a vyhněte odkazující elementů v <xref:System.Windows.Controls.ControlTemplate> kdykoli je to možné.  Pokud jsou správně odpojeného uživatelského rozhraní a logiku vlastního ovládacího prvku, uživatel ovládacího prvku předefinovat ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> přizpůsobit její vzhled. I když vytváření vlastní <xref:System.Windows.Controls.Control> není jednoduché, sestavování <xref:System.Windows.Controls.UserControl>, vlastní <xref:System.Windows.Controls.Control> poskytuje nejvíc flexibilitu.  
  
#### <a name="benefits-of-deriving-from-control"></a>Výhody odvozování z ovládacího prvku  
 Vezměte v úvahu odvozování z <xref:System.Windows.Controls.Control> místo použití <xref:System.Windows.Controls.UserControl> třídy, pokud platí jedna z následujících podmínek:  
  
-   Chcete vzhled ovládacího prvku do, lze přizpůsobit pomocí <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Má vaše řízení podporují různé motivy.  
  
### <a name="deriving-from-frameworkelement"></a>Odvozování z FrameworkElement  
 Ovládací prvky, které jsou odvozeny od <xref:System.Windows.Controls.UserControl> nebo <xref:System.Windows.Controls.Control> závisí skládání stávající elementy. Pro mnoho scénářů, to je přijatelného řešení, protože libovolného objektu, který dědí od <xref:System.Windows.FrameworkElement> může být v <xref:System.Windows.Controls.ControlTemplate>. Existují však časy, kdy vzhled ovládacího prvku vyžaduje více než funkce jednoduché element složení. Pro tyto scénáře založenou na komponentu <xref:System.Windows.FrameworkElement> je správnou volbou.  
  
 Existují dvě standardní metody pro vytvoření <xref:System.Windows.FrameworkElement>– na základě komponenty: přímé vykreslení a vlastní element složení. Přímé vykreslování zahrnuje přepsání <xref:System.Windows.UIElement.OnRender%2A> metodu <xref:System.Windows.FrameworkElement> a poskytování <xref:System.Windows.Media.DrawingContext> operace, které explicitně definujte vizuály součásti. Toto je metoda používá <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.Border>. Vlastní element složení zahrnuje použití objekty typu <xref:System.Windows.Media.Visual> k vytváření vzhled příslušné součásti. Příklad, naleznete v části [pomocí objekty DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>Příklad ovládacího prvku v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složení vlastního elementu, který používá. Je také možné kombinovat přímé vykreslování a vlastní element kompozice ve stejný ovládací prvek.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>Výhody odvozování z FrameworkElement  
 Vezměte v úvahu odvozování z <xref:System.Windows.FrameworkElement> pokud platí jedna z následujících podmínek:  
  
-   Budete chtít mít přesné ovládat vzhled ovládacího prvku nad rámec stanovený jednoduché element složení.  
  
-   Chcete definujte vzhled ovládacího prvku tak, že definujete vlastní vykreslení logiku.  
  
-   Chcete-li vytvořit nové způsoby, které překračují co je možné pomocí stávající elementy <xref:System.Windows.Controls.UserControl> a <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Základy vytváření ovládacího prvku  
 Jak je popsáno výše, jedním z nejúčinnějších funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je schopnost nad rámec nastavení základní vlastností ovládacího prvku změnit vzhled a chování, ale stále nebudete muset vytvořit vlastní ovládací prvek. Stylů, vazby dat a funkce aktivační události je možné pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému. Následující části popisují některé postupy, které byste měli postupovat, bez ohledu na modelu můžete použít k vytvoření vlastního ovládacího prvku tak, aby uživatelé vlastního ovládacího prvku můžete použít tyto funkce, stejně jako ovládacího prvku, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Pomocí vlastností závislostí  
 Pokud vlastnost vlastnost závislosti, je možné provést následující akce:  
  
-   Nastavte vlastnost ve stylu.  
  
-   Vazby ke zdroji dat vlastnosti.  
  
-   Použijte dynamické prostředků jako hodnotu vlastnosti.  
  
-   Animace vlastnost.  
  
 Pokud chcete vlastnost ovládacího prvku k podpoře jakýchkoli tuto funkci, měli byste ho implementovat jako vlastnost závislosti. V následujícím příkladu definuje závislost vlastnost s názvem `Value` provedením následujících akcí:  
  
-   Definování <xref:System.Windows.DependencyProperty> identifikátor s názvem `ValueProperty` jako `public` `static` `readonly` pole.  
  
-   Registraci název vlastnosti v systému vlastnost voláním <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, zadat následující:  
  
    -   Název vlastnosti  
  
    -   Typ vlastnosti.  
  
    -   Typ, který vlastní vlastnost.  
  
    -   Metadata pro vlastnost. Metadata obsahuje výchozí hodnotu vlastnosti, <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>.  
  
-   Definování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálku vlastnost s názvem `Value`, což je stejný název, který se použije k registraci vlastnost závislosti implementací vlastnosti `get` a `set` přistupující objekty. Všimněte si, že `get` a `set` přístupové objekty volat pouze <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> v uvedeném pořadí. Doporučujeme, aby přístupové objekty vlastností závislostí neobsahuje další logiku navíc vzhledem k tomu, klienty a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohou obejít přístupové objekty a volání <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> přímo. Například pokud vlastnost je vázán na datové zdroje, vlastnosti `set` přistupujícího objektu není volán.  Nepřidávat další logiku do get a nastavení přístupových objektů, použijte <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, a <xref:System.Windows.PropertyChangedCallback> delegáti reagovat na nebo při změně zkontrolujte hodnotu.  Další informace o těchto zpětná volání, najdete v části [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Zadejte metodu <xref:System.Windows.CoerceValueCallback> s názvem `CoerceValue`. `CoerceValue`zajišťuje, že `Value` je větší nebo rovna hodnotě `MinValue` a menší než nebo rovno `MaxValue`.  
  
-   Zadejte metodu <xref:System.Windows.PropertyChangedCallback>s názvem `OnValueChanged`. `OnValueChanged`vytvoří <xref:System.Windows.RoutedPropertyChangedEventArgs%601> objektu a připraví vyvolat `ValueChanged` směrované události. Směrované události jsou popsané v další části.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Další informace najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Použití směrované události  
 Stejně jako závislost vlastnosti rozšíření představu o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti s další funkce, směrované události rozšířit představu o standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. Když vytvoříte novou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, je také vhodné implementovat událost jako směrované události, protože směrované události podporuje následující chování:  
  
-   Události mohou být zpracovány v nadřazené položky více ovládacích prvků. Pokud je událost probublávání událostí, jedné nadřazené ve stromové struktuře element může přihlásit k události. Autoři aplikace pak můžete použít jednu obslužnou rutinu reagovat na událost více ovládacích prvků. Například, pokud vlastní ovládací prvek je součástí každou položku v <xref:System.Windows.Controls.ListBox> (protože je součástí <xref:System.Windows.DataTemplate>), vývojáři aplikace můžete definovat obslužné rutiny události pro události ovládacího prvku na <xref:System.Windows.Controls.ListBox>. Vždy, když dojde k události na žádném z ovládacích prvků, se nazývá obslužné rutiny události.  
  
-   Směrované události mohou být používány <xref:System.Windows.EventSetter>, což umožňuje vývojáři aplikace k určení obslužná rutina události v rámci styl.  
  
-   Směrované události mohou být používány <xref:System.Windows.EventTrigger>, což je užitečné pro animace vlastnosti pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 V následujícím příkladu definuje směrované události následujícím způsobem:  
  
-   Definování <xref:System.Windows.RoutedEvent> identifikátor s názvem `ValueChangedEvent` jako `public` `static` `readonly` pole.  
  
-   Zaregistrovat směrované události voláním <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> metoda. V příkladu určuje následující informace, když volá <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   Název události je `ValueChanged`.  
  
    -   Strategie směrování je <xref:System.Windows.RoutingStrategy.Bubble>, což znamená, že obslužné rutiny události ve zdroji (objekt, který vyvolává událost) jako první, a poté jsou volány obslužné rutiny událostí na zdroji na nadřazené elementy po sobě, počínaje obslužné rutiny události na nejbližší Nadřazený element.  
  
    -   Typ obslužné rutiny události je <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, sestavené s <xref:System.Decimal> typu.  
  
    -   Typ vlastnícím události je `NumericUpDown`.  
  
-   Veřejná událost s názvem deklarovat `ValueChanged` i deklarace přístupového objektu události. Příklad volání <xref:System.Windows.UIElement.AddHandler%2A> v `add` deklarace přistupujícího objektu a <xref:System.Windows.UIElement.RemoveHandler%2A> v `remove` deklarace přistupujícího objektu používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí služby.  
  
-   Vytvoření chráněného, virtuální metody s názvem `OnValueChanged` , vyvolá `ValueChanged` událostí.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Další informace najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md) a [vytvoření vlastní směrované události](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Vazbu používají  
 Chcete-li oddělit rozhraní ovládacího prvku z svou logikou, zvažte použití datových vazeb. To je zvlášť důležité, pokud definujte vzhled ovládacího prvku pomocí <xref:System.Windows.Controls.ControlTemplate>. Použijete-li datová vazba, je možné k vyloučení potřeby tak, aby odkazovaly konkrétní části uživatelského rozhraní z kódu. Je vhodné, aby se zabránilo odkazy na elementy, které jsou v <xref:System.Windows.Controls.ControlTemplate> vzhledem k tomu, že když kód odkazuje prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.ControlTemplate> změnil, je odkazovaný element mají být zahrnuty v novém <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad aktualizace <xref:System.Windows.Controls.TextBlock> z `NumericUpDown` řízení, název přiřazení k němu a odkazování na textové pole podle názvu v kódu.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 Následující příklad používá k provádění samé vazby.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Návrh pro návrháře  
 Pokud chcete získat podporu pro vlastní ovládacích prvků WPF v [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (například v okně Vlastnosti pro úpravy vlastností), postupujte podle následujících pokynů.  Další informace o vývoji pro [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], najdete v části [WPF Designer](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).  
  
#### <a name="dependency-properties"></a>Vlastnosti závislosti  
 Je nutné implementovat [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` a `set` přístupových objektů, jak je popsáno dříve, v "Použití závislostí vlastnosti." Návrháři mohou používat obálku pro zjištění přítomnosti vlastnost závislosti, ale jejich, jako je třeba [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a klienti ovládacího prvku, není nutné volat přístupové objekty při získání nebo nastavení vlastnosti.  
  
#### <a name="attached-properties"></a>Přidružené vlastnosti  
 Měli byste implementovat přidružené vlastnosti na vlastní ovládací prvky pomocí následujících pokynů:  
  
-   Mít `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formuláře *PropertyName* `Property` , byl vytváření s použitím <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda. Název vlastnosti, který je předán <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musí odpovídat *PropertyName*.  
  
-   Implementovat pár `public` `static` metod modulu CLR s názvem `Set` *PropertyName* a `Get` *PropertyName*. Obě metody by měla přijímat třídy odvozené od <xref:System.Windows.DependencyProperty> jako jejich první argument. `Set` *PropertyName* metoda přijímá také argument jehož typ odpovídá registrované datového typu pro vlastnost. `Get` *PropertyName* metoda by měla vrátit hodnotu stejného typu. Pokud `Set` *PropertyName* chybí metoda, vlastnost je označen jen pro čtení.  
  
-   `Set`*PropertyName* a `Get` *PropertyName* musí směrovat přímo na <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> metody na závislost cílového objektu. Návrháři může přístup připojená vlastnost voláním prostřednictvím obálku metoda nebo vytvořit přímé volání na objekt cíle závislostí.  
  
 Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Definice a používání sdílených prostředků  
 Můžete zahrnout vlastního ovládacího prvku ve stejném sestavení jako aplikace, nebo můžete balíček ovládacího prvku v samostatné sestavení, které mohou být používány více aplikací. Ve většině případů informace popsané v tomto tématu platí bez ohledu na metodu, kterou používáte.  Ale je potřeba poznamenat, jeden rozdíl.  Po vložení ovládacího prvku ve stejném sestavení jako aplikace, jste volné globální prostředky přidejte do souboru App.xaml. Ale sestavení, které obsahuje pouze ovládací prvky nemá <xref:System.Windows.Application> objekt přidružený, takže soubor App.xaml není k dispozici.  
  
 Aplikace vyhledá prostředku, vypadá na třech úrovních v následujícím pořadí:  
  
1.  Element úroveň.  
  
     Systém začíná elementu, který odkazuje na prostředek a pak prohledá prostředky logické nadřazené a tak dále, dokud nebude dosaženo kořenový element.  
  
2.  Na úrovni aplikace.  
  
     Prostředky, které jsou definované <xref:System.Windows.Application> objektu.  
  
3.  Úroveň motivu.  
  
     Motiv úrovni slovníky jsou uloženy v podsložce s názvem motivů.  Soubory ve složce motivy odpovídají motivů.  Například můžete mít Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml a tak dále.  Můžete taky nechat soubor s názvem generic.xaml.  Když systém hledá prostředek na úrovni motivy, nejprve hledá ho v souboru specifické pro motiv a pak ho bude hledat v generic.xaml.  
  
 Pokud je vaše řízení v sestavení, které jsou oddělené od aplikace, musíte umístit globální prostředky na úrovni element nebo na úrovni motivu. Obě metody mají své výhody.  
  
#### <a name="defining-resources-at-the-element-level"></a>Definování zdroje na úrovni – Element  
 Sdílené prostředky na úrovni element můžete definovat vytvořením slovník vlastní prostředek a slučování s slovník prostředků ovládacího prvku.  Pokud použijete tuto metodu, zadáte název souboru prostředků, který nic, co chcete a může být ve stejné složce jako vaše ovládací prvky. Jednoduché řetězce prostředků na úrovni element můžete také použít jako klíče. Následující příklad vytvoří <xref:System.Windows.Media.LinearGradientBrush> zdrojový soubor s názvem Dictionary1.xaml.  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Jakmile definujete slovníku, budete muset sloučit s slovník prostředků ovládacího prvku.  Můžete to provést pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.  
  
 Následující příklad sloučí slovník prostředků, a pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Nevýhodou tohoto přístupu je, že <xref:System.Windows.ResourceDictionary> objekt se vytvoří pokaždé, když můžete na něj odkazovat.  Například pokud máte 10 vlastní ovládací prvky v knihovně a sloučení slovnících sdílených prostředků pro každý ovládací prvek s použitím jazyka XAML, můžete vytvořit 10 identické <xref:System.Windows.ResourceDictionary> objekty.  To se můžete vyhnout tak, že vytvoříte statické třídu, která sloučí prostředky v kódu a vrátí výsledný <xref:System.Windows.ResourceDictionary>.  
  
 Následující příklad vytvoří třídu, která vrátí sdílenou <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Následující příklad sloučí sdílený prostředek s prostředky vlastního ovládacího prvku v konstruktoru ovládacího prvku zavolá `InitializeComponent`.  Protože `SharedDictionaryManager.SharedDictionary` je pomocí statické vlastnosti, <xref:System.Windows.ResourceDictionary> je vytvořen pouze jednou. Protože slovníku prostředku byl sloučit před `InitializeComponent` byla volána, prostředky jsou k dispozici do ovládacího prvku v jeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru.  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Definování zdroje na úrovni motiv  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Umožňuje vytvořit prostředky pro různé motivy systému Windows.  Jako autor řízení můžete definovat prostředků pro konkrétní motiv Změna vzhledu ovládacího prvku v závislosti na tom, jaký motiv se používá. Například vzhled <xref:System.Windows.Controls.Button> na portálu Classic Windows motiv (výchozí motiv pro systém Windows 2000) se liší od <xref:System.Windows.Controls.Button> v motivu vzhled Luna systému Windows (výchozí motiv pro systém Windows XP) protože <xref:System.Windows.Controls.Button> používá jiné <xref:System.Windows.Controls.ControlTemplate> pro každý motiv.  
  
 Prostředky, které jsou specifické pro motiv udržovaly v slovník prostředků s určitým názvem souboru. Tyto soubory musí být ve složce s názvem `Themes` který je podsložkou složky, která obsahuje ovládací prvek. Následující tabulka uvádí soubory slovník prostředků a motivu, který je přidružen každého souboru:  
  
|Název souboru slovníku prostředku|Motiv systému Windows|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Classic systém Windows 9 x / 2000 podívejte se na systému Windows XP|  
|`Luna.NormalColor.xaml`|Výchozí blue motiv na systému Windows XP|  
|`Luna.Homestead.xaml`|Olivového motiv na systému Windows XP|  
|`Luna.Metallic.xaml`|Stříbrná motiv na systému Windows XP|  
|`Royale.NormalColor.xaml`|Výchozí motiv na systém Windows Media Center|  
|`Aero.NormalColor.xaml`|Výchozí motiv v systému Windows Vista|  
  
 Není nutné definovat prostředku pro každý motiv. Pokud pro konkrétní motiv není definován prostředek, pak ovládací prvek kontroluje `Classic.xaml` pro prostředek. Pokud prostředek není definován v souboru, který odpovídá aktuálního motivu nebo v `Classic.xaml`, ovládacího prvku používá obecný prostředek, který se v souboru slovníku prostředků s názvem `generic.xaml`.  `generic.xaml` Soubor je umístěný ve stejné složce jako soubory slovník prostředků specifické pro motiv. I když `generic.xaml` neodpovídá na konkrétní motiv systému Windows, je stále slovník úrovni motivu.  
  
 [NumericUpDown – ovládací prvek vlastní motiv a ukázkové podpora automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=160025) obsahuje dvě slovnících prostředků pro `NumericUpDown` ovládacího prvku: jeden je v generic.xaml a jeden v Luna.NormalColor.xaml.  Můžete spustit aplikace a přepínat mezi stříbrným motiv v systému Windows XP a jiné motiv zobrazíte rozdílu mezi šablonami dvě ovládacího prvku. (Pokud používáte systém Windows Vista, můžete přejmenovat Luna.NormalColor.xaml Aero.NormalColor.xaml a přepínat mezi dvěma motivy, jako jsou klasické a výchozí motiv pro systém Windows Vista.)  
  
 Když vložíte <xref:System.Windows.Controls.ControlTemplate> v některém z soubory slovník specifické pro motiv prostředků, musíte vytvořit statického konstruktoru pro řízení a volání <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metodu <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definování a odkazování na klíče pro motiv prostředky  
 Když definujete prostředek na úrovni element, můžete přiřadit řetězec jako svůj klíč a přístup k prostředku prostřednictvím řetězec. Když definujete prostředek na úrovni motiv, je nutné použít <xref:System.Windows.ComponentResourceKey> jako klíč.  V následujícím příkladu definuje generic.xaml prostředku.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 V následujícím příkladu odkazuje prostředek zadáním <xref:System.Windows.ComponentResourceKey> jako klíč.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Určení umístění prostředků motiv  
 Najít prostředky pro ovládací prvek, hostování aplikace musí vědět, že sestavení obsahuje prostředky pro konkrétní ovládací prvek. Můžete provést přidáním <xref:System.Windows.ThemeInfoAttribute> na sestavení, které obsahuje ovládací prvek. <xref:System.Windows.ThemeInfoAttribute> Má <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> vlastnost, která určuje umístění obecné zdroje a <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> vlastnost, která určuje umístění prostředků specifických pro motiv.  
  
 Následující příklad nastavuje <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> a <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> vlastnosti, které chcete <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, chcete-li určit, zda jsou prostředky obecné a specifické pro motiv ve stejném sestavení jako ovládací prvek.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Viz také  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
