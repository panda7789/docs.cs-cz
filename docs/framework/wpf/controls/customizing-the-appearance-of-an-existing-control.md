---
title: "Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate"
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
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5455007e407bf4320355aebfd043bfc056d6d56
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate
<a name="introduction"></a>A <xref:System.Windows.Controls.ControlTemplate> určuje vizuální strukturu a visual chování ovládacího prvku. Můžete přizpůsobit vzhled ovládacího prvku tím, že it a nové <xref:System.Windows.Controls.ControlTemplate>. Při vytváření <xref:System.Windows.Controls.ControlTemplate>, nahraďte vzhled ovládacího prvku existující beze změny jeho funkci. Například můžete provést tlačítka ve vaší aplikaci zaokrouhlí místo výchozí odmocnina tvar, ale bude stále vyvolat tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 Toto téma vysvětluje různé součásti <xref:System.Windows.Controls.ControlTemplate>, ukazuje vytvoření jednoduché <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>a vysvětluje, jak porozumět kontrakt řízení ovládacího prvku, abyste si můžete přizpůsobit její vzhled. Vzhledem k tomu, že vytvoříte <xref:System.Windows.Controls.ControlTemplate> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete změnit vzhled ovládacího prvku bez psaní jakéhokoli kódu. Návrhář, jako je například Microsoft Expression Blend, můžete taky vytvořit vlastní ovládací prvek šablony. Toto téma ukazuje, příklady v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , přizpůsobení vzhledu <xref:System.Windows.Controls.Button> a jsou uvedené kompletní příklad na konci tohoto tématu. Další informace o používání Expression Blend najdete v tématu [styly ovládacího prvku, který podporuje šablony](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Následující ilustrace zobrazení <xref:System.Windows.Controls.Button> používající <xref:System.Windows.Controls.ControlTemplate> vytvořený v tomto tématu.  
  
 ![Tlačítko s šablonu vlastního ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá šablonu vlastního ovládacího prvku  
  
 ![Tlačítko červené ohraničení. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá šablonu vlastního ovládacího prvku a má ukazatel myši nad ním  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že když chápete, jak vytvořit a používat ovládací prvky a stylů, jak je popsáno v [ovládací prvky](../../../../docs/framework/wpf/controls/index.md). Principy probírané v tomto tématu se vztahují na elementy, které dědí od <xref:System.Windows.Controls.Control> třída, s výjimkou <xref:System.Windows.Controls.UserControl>. Nelze použít <xref:System.Windows.Controls.ControlTemplate> k <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Když měli byste vytvořit ControlTemplate  
 Ovládací prvky mít mnoho vlastností, jako <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, a <xref:System.Windows.Controls.Control.FontFamily%2A>, které můžete nastavit, aby zadejte různé aspekty vzhledu ovládacího prvku, ale změny, které můžete vytvořit pomocí nastavení těchto vlastností jsou omezené. Například můžete nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na modrou a <xref:System.Windows.Controls.Control.FontStyle%2A> na kurzíva na <xref:System.Windows.Controls.CheckBox>.  
  
 Bez možnosti pro vytvoření nového <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvky, všechny ovládací prvky v každé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace by mít stejné celkový vzhled, což omezí možnost vytváření aplikací s vlastní vzhled a chování. Ve výchozím nastavení každý <xref:System.Windows.Controls.CheckBox> má podobnou charakteristikou. Například obsah <xref:System.Windows.Controls.CheckBox> je vždy napravo od indikátor výběru a zaškrtnutí vždy slouží k označení, že <xref:System.Windows.Controls.CheckBox> je vybrána.  
  
 Vytváření <xref:System.Windows.Controls.ControlTemplate> Pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec jaké nastavení jiné vlastnosti na ovládací prvek provede. V příkladu <xref:System.Windows.Controls.CheckBox>, Předpokládejme, že chcete obsah zaškrtnutím políčka nad indikátor výběru být a chcete, aby X, která označuje, že <xref:System.Windows.Controls.CheckBox> je vybrána. Zadejte tyto změny v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.CheckBox>.  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.CheckBox> používající výchozí <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Zaškrtávací políčko s výchozí šablony ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaškrtávací políčko, který používá výchozí šablonu pro ovládací prvek  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.CheckBox> používající vlastní <xref:System.Windows.Controls.ControlTemplate> umístit obsah <xref:System.Windows.Controls.CheckBox> nad indikátor výběru a zobrazí X při <xref:System.Windows.Controls.CheckBox> je vybrána.  
  
 ![Zaškrtávací políčko se šablonou vlastního ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaškrtávací políčko, který používá šablonu vlastního ovládacího prvku  
  
 <xref:System.Windows.Controls.ControlTemplate> Pro <xref:System.Windows.Controls.CheckBox> v této ukázce je poměrně složité, takže toto téma používá jednodušší příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Změna strukturu Visual ovládacího prvku  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ovládacího prvku je často složený <xref:System.Windows.FrameworkElement> objekty. Při vytváření <xref:System.Windows.Controls.ControlTemplate>, zkombinujete <xref:System.Windows.FrameworkElement> objekty, které chcete vytvořit jeden ovládací prvek. A <xref:System.Windows.Controls.ControlTemplate> musí mít jenom jeden <xref:System.Windows.FrameworkElement> jako jeho kořenový element. Kořenový element obvykle obsahuje jiné <xref:System.Windows.FrameworkElement> objekty. Kombinace objektů, které tvoří visual struktura ovládacího prvku.  
  
 Následující příklad vytvoří vlastní <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Vytvoří visual strukturu <xref:System.Windows.Controls.Button>. Tento příklad nezmění vzhled tlačítka, při přesunutí ukazatele myši nad ním nebo klikněte na něj. Změna vzhledu tlačítka, pokud je v jiném stavu, je popsána dále v tomto tématu.  
  
 V tomto příkladu visual struktura se skládá z následujících částí:  
  
-   A <xref:System.Windows.Controls.Border> s názvem `RootElement` sloužícím jako kořenové šablony <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> tedy podřízenou `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> , zobrazí obsah, na tlačítko. <xref:System.Windows.Controls.ContentPresenter> Umožňuje jakéhokoli typu objektu, který se má zobrazit.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachování funkce vlastností ovládacího prvku pomocí TemplateBinding  
 Když vytvoříte novou <xref:System.Windows.Controls.ControlTemplate>, stále můžete použít veřejné vlastnosti Pokud chcete změnit vzhled ovládacího prvku. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) vlastnost element, který je v váže – rozšíření značek <xref:System.Windows.Controls.ControlTemplate> veřejné vlastnosti, která je definována pomocí ovládacího prvku. Při použití [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), povolte vlastnosti v ovládacím prvku tak, aby fungoval jako parametry šablony. To znamená, pokud je nastavená vlastnost u prvku, zda hodnota dojde k předání elementu, který má [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) na něm.  
  
 V následujícím příkladu se opakuje součástí v předchozím příkladu, který používá [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) – rozšíření značek pro vazbu vlastnosti elementů, které jsou v <xref:System.Windows.Controls.ControlTemplate> na veřejné vlastnosti, které jsou definovány na tlačítko.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 V tomto příkladu <xref:System.Windows.Controls.Grid> má jeho <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost šablony vázána na <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Protože <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> je šablona vázán, můžete vytvořit více tlačítek, které používají stejné <xref:System.Windows.Controls.ControlTemplate> a nastavte <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> různých hodnot na každé tlačítko. Pokud <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> byla šablona není vázána na vlastnost v elementu <xref:System.Windows.Controls.ControlTemplate>, nastavení <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> tlačítka by mělo mít žádný vliv na vzhled tlačítka.  
  
 Všimněte si, že názvy dvě vlastnosti nemusí být stejné. V předchozím příkladu <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Controls.Button> šablony je vázán k <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Controls.ContentPresenter>. To umožňuje obsah na tlačítko se umístí vodorovně. <xref:System.Windows.Controls.ContentPresenter>nemá vlastnost s názvem `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> mohou být vázány na <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Při šablony můžete vytvořit vazbu vlastnosti, se ujistěte, že zdrojové a cílové vlastnosti jsou stejného typu.  
  
 <xref:System.Windows.Controls.Control> Třída definuje několik vlastností, které se mají použít šablonu ovládacího prvku mít vliv na ovládací prvek, pokud jsou nastavená. Jak <xref:System.Windows.Controls.ControlTemplate> používá vlastnost závisí na vlastnosti. <xref:System.Windows.Controls.ControlTemplate> Musí používat vlastnost v jednom z následujících způsobů:  
  
-   Element v <xref:System.Windows.Controls.ControlTemplate> šablony váže k vlastnosti.  
  
-   Element v <xref:System.Windows.Controls.ControlTemplate> dědí vlastnosti z nadřazené <xref:System.Windows.FrameworkElement>.  
  
 Následující tabulka uvádí visual vlastnosti děděny z ovládacího prvku <xref:System.Windows.Controls.Control> třídy. Také určuje, zda výchozí šablony řízení ovládacího prvku používá hodnotu zděděné vlastnosti nebo pokud musí být vázána šablony.  
  
|Vlastnost|Použití – metoda|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Šablona vazby|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Šablona vazby|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Šablona vazby|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Dědičnost vlastnosti nebo šablony vazby|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Dědičnost vlastnosti nebo šablony vazby|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Dědičnost vlastnosti nebo šablony vazby|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Dědičnost vlastnosti nebo šablony vazby|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Dědičnost vlastnosti nebo šablony vazby|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Šablona vazby|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Šablona vazby|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Šablona vazby|  
  
 V tabulce jsou uvedeny pouze visual vlastnosti zděděno z <xref:System.Windows.Controls.Control> třídy. Kromě vlastností uvedených v tabulce, mohou také dědit ovládacího prvku <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, a <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> vlastnosti z nadřazeného elementu framework.  
  
 Navíc pokud <xref:System.Windows.Controls.ContentPresenter> v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> automaticky vytvoří vazbu <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti. Podobně <xref:System.Windows.Controls.ItemsPresenter> který se v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ItemsControl> automaticky vytvoří vazbu <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.ItemsPresenter> vlastnosti.  
  
 Následující příklad vytvoří dvě tlačítka, které používají <xref:System.Windows.Controls.ControlTemplate> definované v předchozím příkladu. V příkladu je nastavena <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, a <xref:System.Windows.Controls.Control.FontSize%2A> vlastnosti na každé tlačítko. Nastavení <xref:System.Windows.Controls.Control.Background%2A> vlastnost má vliv, protože je vázán v šabloně <xref:System.Windows.Controls.ControlTemplate>. I když <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> vlastnosti nejsou šablony vázán, je nastavení má vliv, protože jsou děděné jejich hodnot.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 V předchozím příkladu vytváří výstup, který je podobný na následujícím obrázku.  
  
 ![Dvě tlačítka, jeden blue a druhé fialové. ] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dvě tlačítka pomocí různých barev pozadí  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Změna vzhledu ovládacího prvku v závislosti na stavu  
 Rozdíl mezi tlačítka s jeho výchozí vzhled a v předchozím příkladu je, že výchozí tlačítko mírně změní, když je v různých stavů. Například výchozí tlačítko vzhled změní při stisknutí tlačítka nebo když ukazatel myši nad tlačítko. I když <xref:System.Windows.Controls.ControlTemplate> nezmění funkce ovládacího prvku mění chování visual ovládacího prvku. Visual chování popisuje vzhledu ovládacího prvku, pokud je v určitých stavu. Abyste pochopili rozdíl mezi visual chování ovládacího prvku a funkcí, podívejte se na příklad tlačítko. Funkce na tlačítko se má vyvolat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v případě, že po kliknutí na, ale je visual chování na tlačítko změnit její vzhled, pokud je na odkazuje nebo stisknutí tlačítka.  
  
 Používáte <xref:System.Windows.VisualState> objekty k určení vzhledu ovládacího prvku, pokud je v určitých stavu. A <xref:System.Windows.VisualState> obsahuje <xref:System.Windows.Media.Animation.Storyboard> , mění vzhled prvky, které jsou v <xref:System.Windows.Controls.ControlTemplate>. Nemáte psaní jakéhokoli kódu se dojít, protože logiku ovládacího prvku změní stav pomocí <xref:System.Windows.VisualStateManager>. Pokud ovládací prvek vstupuje do stavu, která je zadána <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> vlastnost, <xref:System.Windows.Media.Animation.Storyboard> začne. Při ukončení řízení stavu, <xref:System.Windows.Media.Animation.Storyboard> zastaví.  
  
 Následující příklad ukazuje <xref:System.Windows.VisualState> , mění vzhled <xref:System.Windows.Controls.Button> po ukazatel myši nad ním. <xref:System.Windows.Media.Animation.Storyboard> Změní barvu ohraničení tlačítka tak, že změníte barvu `BorderBrush`. Pokud vyhledáváte <xref:System.Windows.Controls.ControlTemplate> příklad na začátku tohoto tématu, bude odvolat, který `BorderBrush` je název <xref:System.Windows.Media.SolidColorBrush> přiřazené <xref:System.Windows.Controls.Border.Background%2A> z <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Ovládací prvek je zodpovědná za definování stavy jako součást jeho řízení kontrakt, který je podrobněji v [přizpůsobení další ovládací prvky podle Principy řízení kontrakt](#customizing_other_controls_by_understanding_the_control_contract) dál v tomto tématu. Následující tabulka uvádí stavy, které jsou určené pro <xref:System.Windows.Controls.Button>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad ovládacího prvku.|  
|Stisknutí tlačítka|CommonStates|Stisknutí ovládacího prvku.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Zaměřuje|FocusStates|Ovládací prvek má právě fokus.|  
|Nezaostřená|FocusStates|Ovládací prvek nemá fokus.|  
  
 <xref:System.Windows.Controls.Button> Definuje dvě skupiny stavu: `CommonStates` skupina obsahuje `Normal`, `MouseOver`, `Pressed`, a `Disabled` stavy. `FocusStates` Skupina obsahuje `Focused` a `Unfocused` stavy. Stavy ve stejné skupině stavu se vzájemně vylučují. Ovládací prvek, je vždy přesně jeden stav na skupinu. Například <xref:System.Windows.Controls.Button> může být vybrán jako aktivní, i když ukazatel myši není přes, takže <xref:System.Windows.Controls.Button> v `Focused` stavu může být v `MouseOver`, `Pressed`, nebo `Normal` stavu.  
  
 Přidání <xref:System.Windows.VisualState> objekty ke <xref:System.Windows.VisualStateGroup> objekty. Přidání <xref:System.Windows.VisualStateGroup> objekty ke <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost. V následujícím příkladu definuje <xref:System.Windows.VisualState> pro objekty `Normal`, `MouseOver`, a `Pressed` stavy, které jsou v `CommonStates` skupiny. <xref:System.Windows.VisualState.Name%2A> Jednotlivých <xref:System.Windows.VisualState> odpovídá názvu v předchozí tabulce. `Disabled` Stavu a stavů v `FocusStates` skupiny byly vynechány zachovat krátké příklad, ale jsou zahrnuty v celé příkladu na konci tohoto tématu.  
  
> [!NOTE]
>  Nastavte <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost v kořenovém <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 V předchozím příkladu vytváří výstup, který je podobný následující ilustrace.  
  
 ![Tlačítko s šablonu vlastního ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá šablonu vlastního ovládacího prvku v normálním stavu  
  
 ![Tlačítko červené ohraničení. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá šablonu vlastního ovládacího prvku v myši nad stavu  
  
 ![Ohraničení je transparentní na stisknutého tlačítka. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Tlačítko, které používá šablonu vlastního ovládacího prvku ve stavu při stisknutí tlačítka  
  
 Najít visual stavy pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [– styly ovládacích prvků a šablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Určení chování ovládacího prvku při přechází mezi stavy  
 V předchozím příkladu vzhled tlačítka také změní, když uživatel klikne, ale pokud stisknutí tlačítka pro celou sekundu uživatel nezná účinek. Ve výchozím nastavení trvá animace sekundu proběhnout. Vzhledem k tomu, že budou uživatelé klikněte a uvolnění tlačítka v mnohem méně času, vizuální zpětnou vazbu, se neprojeví, pokud necháte <xref:System.Windows.Controls.ControlTemplate> ve svém výchozím stavu.  
  
 Můžete zadat dobu, jakou trvá animace proběhnout plynule přechodu jeden stav prvku přidáním <xref:System.Windows.VisualTransition> objekty ke <xref:System.Windows.Controls.ControlTemplate>. Při vytváření <xref:System.Windows.VisualTransition>, zadejte jednu nebo více následujících akcí:  
  
-   Čas potřebný pro přechod mezi stavy proběhnout.  
  
-   Další změny vzhledu ovládacího prvku, ke kterým došlo během přechodu.  
  
-   Které stavy <xref:System.Windows.VisualTransition> se použije pro.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Určení trvání přechodu  
 Můžete určit, jak dlouho trvá přechod nastavením <xref:System.Windows.VisualTransition.GeneratedDuration%2A> vlastnost. V předchozím příkladu má <xref:System.Windows.VisualState> který určuje, že se na tlačítko ohraničení transparentní při stisknutí tlačítka, ale animace trvá příliš dlouho byly patrné, pokud je tlačítko rychle stisknutí a vydání. Můžete použít <xref:System.Windows.VisualTransition> zadat dobu trvá ovládacího prvku přechod do stavu při stisknutí tlačítka. Následující příklad určuje, že ovládací prvek trvá setiny druhý uvést do stavu při stisknutí tlačítka.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Zadání změny vzhledu ovládacího prvku během přechodu  
 <xref:System.Windows.VisualTransition> Obsahuje <xref:System.Windows.Media.Animation.Storyboard> , která začíná při řízení přechody mezi stavy. Například můžete zadat, že určité animace nastane, když ovládacího prvku přejde z `MouseOver` do stavu `Normal` stavu. Následující příklad vytvoří <xref:System.Windows.VisualTransition> který určuje, že pokud se uživatel přesune ukazatel myši z tlačítka, ohraničení na tlačítko se změní blue, pak na žlutou, dále na černé půl sekundy.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Určení, kdy je použit VisualTransition  
 A <xref:System.Windows.VisualTransition> lze omezit na týkají pouze určité stavy, nebo ji jde použít kdykoli řízení přechodů mezi stavy. V předchozím příkladu <xref:System.Windows.VisualTransition> se použije v případě, že ovládací prvek přejde z `MouseOver` stavu na `Normal` stavu; v příkladu před <xref:System.Windows.VisualTransition> se použije v případě, že ovládací prvek přejde do `Pressed` stavu. Pokud omezíte <xref:System.Windows.VisualTransition> platí nastavením <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A> vlastnosti. Následující tabulka popisuje úrovněmi omezení nejvíc omezující k nejméně omezující.  
  
|Typ omezení|Hodnota z|Hodnota k|  
|-------------------------|-------------------|-----------------|  
|Ze zadané stavu do jiného zadaného stavu|Název<xref:System.Windows.VisualState>|Název<xref:System.Windows.VisualState>|  
|Ze všech stavu do zadaného stavu|Nenastaveno|Název<xref:System.Windows.VisualState>|  
|Ze zadané stavu k některému ze stavů|Název<xref:System.Windows.VisualState>|Nenastaveno|  
|Ze všech jiných stavu|Nenastaveno|Nenastaveno|  
  
 Můžete mít více <xref:System.Windows.VisualTransition> objekty v <xref:System.Windows.VisualStateGroup> který odkazovat do stejného stavu, ale používají v pořadí, v předchozí tabulce určuje. V následujícím příkladu jsou uvedeny dvě <xref:System.Windows.VisualTransition> objekty. Když ovládacího prvku přejde z `Pressed` stavu na `MouseOver` stavu, <xref:System.Windows.VisualTransition> má oba <xref:System.Windows.VisualTransition.From%2A> a <xref:System.Windows.VisualTransition.To%2A> sada slouží. Když se ovládací prvek přejde ze stavu, který není `Pressed` k `MouseOver` stav, se používá jiný stav.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Má <xref:System.Windows.VisualStateGroup.Transitions%2A> vlastnost, která obsahuje <xref:System.Windows.VisualTransition> objekty, které platí pro <xref:System.Windows.VisualState> objekty v <xref:System.Windows.VisualStateGroup>. Jako <xref:System.Windows.Controls.ControlTemplate> Autor se volné k zahrnutí všech <xref:System.Windows.VisualTransition> chcete. Ale pokud <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A> vlastnosti jsou nastaveny na stav názvy, které nejsou v <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> je ignorována.  
  
 Následující příklad ukazuje <xref:System.Windows.VisualStateGroup> pro `CommonStates`. V příkladu je definován <xref:System.Windows.VisualTransition> pro každé z následujících tlačítka přechází.  
  
-   Na `Pressed` stavu.  
  
-   Na `MouseOver` stavu.  
  
-   Z `Pressed` do stavu `MouseOver` stavu.  
  
-   Z `MouseOver` do stavu `Normal` stavu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Přizpůsobení další ovládací prvky podle pochopení kontrakt ovládací prvek  
 Ovládací prvek, který používá <xref:System.Windows.Controls.ControlTemplate> zadat jeho visual struktura (pomocí <xref:System.Windows.FrameworkElement> objekty) a visual chování (pomocí <xref:System.Windows.VisualState> objekty) používá model řízení částí. Řadu ovládacích prvků, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 pomocí tohoto modelu. Části, <xref:System.Windows.Controls.ControlTemplate> Autor musí mít na paměti, které se předávají prostřednictvím řízení kontrakt. Až porozumíte části kontraktu ovládací prvek, můžete přizpůsobit vzhled libovolný ovládací prvek, který používá model řízení částí.  
  
 Ovládací prvek kontrakt má tři prvky:  
  
-   Vizuální prvky, které používá logiku ovládacího prvku.  
  
-   Stavy ovládacího prvku a skupiny, ke které patří každý stav.  
  
-   Veřejné vlastnosti vizuálně ovlivňující ovládacího prvku.  
  
### <a name="visual-elements-in-the-control-contract"></a>Vizuální prvky v kontraktu ovládací prvek  
 Někdy ovládacího prvku logiku komunikuje se službou <xref:System.Windows.FrameworkElement> který se v <xref:System.Windows.Controls.ControlTemplate>. Například ovládací prvek může zpracovat událost jednoho z jeho elementy. Když se očekává, že ovládacího prvku najít konkrétní <xref:System.Windows.FrameworkElement> v <xref:System.Windows.Controls.ControlTemplate>, ho musí sdělit <xref:System.Windows.Controls.ControlTemplate> autora. Ovládací prvek používá <xref:System.Windows.TemplatePartAttribute> k předání typu element, který se očekává a co by měl být název elementu. <xref:System.Windows.Controls.Button> Nemá <xref:System.Windows.FrameworkElement> částí v její řízení smlouvy, ale další ovládací prvky, jako <xref:System.Windows.Controls.ComboBox>, provést.  
  
 Následující příklad ukazuje <xref:System.Windows.TemplatePartAttribute> objekty, které jsou zadány na <xref:System.Windows.Controls.ComboBox> třídy. Logiku <xref:System.Windows.Controls.ComboBox> očekává <xref:System.Windows.Controls.TextBox> s názvem `PART_EditableTextBox` a <xref:System.Windows.Controls.Primitives.Popup> s názvem `PART_Popup` v jeho <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Následující příklad ukazuje zjednodušené <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ComboBox> , obsahuje prvky, které jsou určené <xref:System.Windows.TemplatePartAttribute> objekty na <xref:System.Windows.Controls.ComboBox> – třída.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stavy v kontraktu ovládací prvek  
 Stavy ovládacího prvku jsou taky součástí kontraktu ovládacího prvku. Příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ukazuje, jak určit vzhled <xref:System.Windows.Controls.Button> v závislosti na stavech. Vytváření <xref:System.Windows.VisualState> pro každý zadaný stav a uveďte všechny <xref:System.Windows.VisualState> objekty tuto sdílenou složku <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> v <xref:System.Windows.VisualStateGroup>, jak je popsáno v [Změna vzhledu ovládacího prvku závislosti na její stav](#changing_the_appearance_of_a_control_depending_on_its_state) starší v tomto téma. Ovládací prvky třetích stran by měl určovat stavy pomocí <xref:System.Windows.TemplateVisualStateAttribute>, což umožňuje návrhářské nástroje, jako je například Expression Blend vystavit stavy ovládacího prvku k vytváření šablon ovládacího prvku.  
  
 Najít ovládací prvek kontrakt pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [– styly ovládacích prvků a šablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Vlastnosti v kontraktu ovládací prvek  
 Veřejné vlastnosti, které vizuálně ovlivňují ovládacího prvku jsou také uvedené v řízení kontrakt. Můžete nastavit tyto vlastnosti Změna vzhledu ovládacího prvku bez vytvoření nové <xref:System.Windows.Controls.ControlTemplate>. Můžete také [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) – rozšíření značek pro vazbu vlastnosti elementů, které jsou v <xref:System.Windows.Controls.ControlTemplate> na veřejné vlastnosti, které jsou definovány <xref:System.Windows.Controls.Button>.  
  
 Následující příklad ukazuje kontrakt ovládací prvek tlačítko.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate>, je často nejjednodušší začněte s existující <xref:System.Windows.Controls.ControlTemplate> a provést změny. Můžete provést jednu z těchto možností změnit stávající <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Pomocí návrháře, jako je například Expression Blend, které poskytuje grafické uživatelské rozhraní pro vytváření šablon ovládacích prvků. Další informace najdete v tématu [styly ovládacího prvku, který podporuje šablony](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Získat výchozí <xref:System.Windows.Controls.ControlTemplate> a upravit ho. Najít výchozí šablony řízení, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [výchozí WPF motivy](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> zmiňované v tomto tématu.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Viz také  
 [Stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md)
