---
title: Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate
ms.date: 03/30/2017
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
ms.openlocfilehash: 435789e0d1bc601a9eb51488254407fefd334e05
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483811"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate
<a name="introduction"></a> A <xref:System.Windows.Controls.ControlTemplate> určuje vizuální struktury a chování ovládacího prvku visual. Můžete přizpůsobit vzhled ovládacího prvku tak, že udělíte it nový <xref:System.Windows.Controls.ControlTemplate>. Když vytvoříte <xref:System.Windows.Controls.ControlTemplate>, nahraďte vzhledu stávajícího ovládacího prvku beze změny jeho funkce. Například měli tlačítka ve vaší aplikaci round místo výchozí Čtvereček tvar, ale stále na tlačítko vyvolá <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
 Toto téma vysvětluje různé součásti <xref:System.Windows.Controls.ControlTemplate>, popisuje vytvoření jednoduchého <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>a vysvětluje, jak můžete porozumět kontrakt ovládacího prvku ovládacího prvku tak, aby si můžete přizpůsobit její vzhled. Vzhledem k tomu, že vytvoříte <xref:System.Windows.Controls.ControlTemplate> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aniž byste museli psát jakýkoli kód, můžete změnit vzhled ovládacího prvku. Návrháře, jako je například Microsoft Expression Blend, můžete také použít k vytvoření šablony vlastního ovládacího prvku. Příklady v tomto tématu si ukážeme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , přizpůsobit vzhled <xref:System.Windows.Controls.Button> a uvádí úplném příkladu na konci tohoto tématu. Další informace o používání Expression Blend, naleznete v tématu [práce se styly ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Následující ilustrace <xref:System.Windows.Controls.Button> , která používá <xref:System.Windows.Controls.ControlTemplate> vytvořený v tomto tématu.  
  
 ![Tlačítko se šablonou vlastního ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá šablonu vlastního ovládacího prvku  
  
 ![Tlačítko se červené ohraničení. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá šablonu vlastního ovládacího prvku a má ukazatel myši nad ním  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že vám pochopit, jak vytvořit a používat ovládací prvky a stylů, jak je popsáno v [ovládací prvky](../../../../docs/framework/wpf/controls/index.md). Principy probírané v tomto tématu platí pro prvky, které dědí <xref:System.Windows.Controls.Control> třídy, s výjimkou <xref:System.Windows.Controls.UserControl>. Nelze použít <xref:System.Windows.Controls.ControlTemplate> k <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Pokud byste měli vytvořit objektu ControlTemplate  
 Ovládací prvky, jako mají mnoho vlastností <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, a <xref:System.Windows.Controls.Control.FontFamily%2A>, můžete nastavit na určit různé aspekty vzhledu ovládacího prvku, ale změny, které můžete vytvořit pomocí nastavení těchto vlastností jsou omezené. Například můžete nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na modrou a <xref:System.Windows.Controls.Control.FontStyle%2A> na kurzíva na <xref:System.Windows.Controls.CheckBox>.  
  
 Kdybychom neměli možnost vytvořit novou <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvky, všechny ovládací prvky v každé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace bude mít stejný celkový vzhled, který omezí možnost vytvářet aplikace s vlastní vzhled a chování. Ve výchozím nastavení každý <xref:System.Windows.Controls.CheckBox> má podobnou charakteristikou. Například obsah <xref:System.Windows.Controls.CheckBox> je vždy napravo od indikátor výběru a zaškrtávací políčko se vždy používá k označení, že <xref:System.Windows.Controls.CheckBox> zaškrtnuto.  
  
 Vytváření <xref:System.Windows.Controls.ControlTemplate> Pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec doporučení dělají, jaká nastavení vlastnosti na ovládacím prvku. V příkladu <xref:System.Windows.Controls.CheckBox>, Předpokládejme, že chcete, aby obsah zaškrtnutím políčka být vyšší než indikátor výběru a chcete, aby X označuje, že <xref:System.Windows.Controls.CheckBox> zaškrtnuto. Zadejte tyto změny v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.CheckBox>.  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.CheckBox> , který používá výchozí <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Zaškrtávací políčko pomocí výchozí šablony ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaškrtávací políčko, který používá výchozí šablonu ovládacího prvku  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.CheckBox> , která používá vlastní <xref:System.Windows.Controls.ControlTemplate> umístit obsah <xref:System.Windows.Controls.CheckBox> nad indikátor výběru a zobrazí X při <xref:System.Windows.Controls.CheckBox> je vybraná.  
  
 ![Zaškrtávací políčko se šablonou vlastního ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaškrtávací políčko, který používá šablonu vlastního ovládacího prvku  
  
 <xref:System.Windows.Controls.ControlTemplate> Pro <xref:System.Windows.Controls.CheckBox> v tomto příkladu je poměrně složité, takže toto téma používá jednodušší příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Změna vizuální struktury ovládacího prvku  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ovládací prvek je často složeného <xref:System.Windows.FrameworkElement> objekty. Když vytvoříte <xref:System.Windows.Controls.ControlTemplate>, můžete kombinovat <xref:System.Windows.FrameworkElement> objekty sestavit jeden ovládací prvek. A <xref:System.Windows.Controls.ControlTemplate> musí obsahovat pouze jeden <xref:System.Windows.FrameworkElement> jako jeho kořenový element. Kořenový element obvykle obsahuje další <xref:System.Windows.FrameworkElement> objekty. Kombinace objekty tvoří vizuální struktury ovládacího prvku.  
  
 Následující příklad vytvoří vlastní <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Vytvoří vizuální struktury <xref:System.Windows.Controls.Button>. V tomto příkladu se nezmění jeho vzhled při přesunutí ukazatele myši nad ním nebo klikněte na něj. Změna vzhledu tlačítka, když je v jiném stavu jsou popsány dále v tomto tématu.  
  
 V tomto příkladu vizuální struktury se skládá z následujících částí:  
  
-   A <xref:System.Windows.Controls.Border> s názvem `RootElement` , který slouží jako kořen šablony <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> , který je podřízený `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> , který zobrazí obsah na tlačítko. <xref:System.Windows.Controls.ContentPresenter> Umožňuje jakéhokoli typu objektu, který se má zobrazit.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachování funkce vlastností ovládacího prvku s použitím TemplateBinding  
 Když vytvoříte nový <xref:System.Windows.Controls.ControlTemplate>, stále můžete pomocí veřejné vlastnosti můžete změnit vzhled ovládacího prvku. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) vlastnost elementu, který se váže – rozšíření značek <xref:System.Windows.Controls.ControlTemplate> veřejnou vlastnost, která je definována v ovládacím prvku. Při použití [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), povolení vlastností ovládacího prvku tak, aby fungoval jako parametry šablony. To znamená, když je nastavena vlastnost v ovládacím prvku, tato hodnota je předán na element, který má [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) na něj.  
  
 V následujícím příkladu se opakuje součástí předchozí příklad, který používá [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) – rozšíření značek pro vazbu vlastnosti prvků, které jsou v <xref:System.Windows.Controls.ControlTemplate> na veřejné vlastnosti, které jsou definovány na tlačítko.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 V tomto příkladu <xref:System.Windows.Controls.Grid> má jeho <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> šablony vlastnost vázána na <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Protože <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> je šablona vázán, můžete vytvořit více tlačítek, které používají stejné <xref:System.Windows.Controls.ControlTemplate> a nastavit <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> na různé hodnoty v každé tlačítko. Pokud <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> byla šablona není vázána na vlastnost elementu v <xref:System.Windows.Controls.ControlTemplate>a nastavte <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> tlačítko by mít žádný vliv na vzhled na tlačítko.  
  
 Všimněte si, že názvy dvou vlastností nemusí být identické. V předchozím příkladu <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Controls.Button> šablony je vázán na <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Controls.ContentPresenter>. To umožňuje obsahu tlačítka, který se umístil vodorovně. <xref:System.Windows.Controls.ContentPresenter> nemá vlastnost s názvem `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> může být vázaný na <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Když šablony můžete vytvořit vazbu vlastnosti, ujistěte se, že zdrojové a cílové vlastnosti jsou stejného typu.  
  
 <xref:System.Windows.Controls.Control> Třída definuje několik vlastností, které musí používat šablonu ovládacího prvku mají nějaký efekt na ovládacím prvku, když jsou nastavené. Jak <xref:System.Windows.Controls.ControlTemplate> používá vlastnost závisí na vlastnost. <xref:System.Windows.Controls.ControlTemplate> Musíte použít vlastnost v jednom z následujících způsobů:  
  
-   V elementu <xref:System.Windows.Controls.ControlTemplate> šablona vytvoří vazbu na vlastnost.  
  
-   V elementu <xref:System.Windows.Controls.ControlTemplate> dědí vlastnosti z nadřazené položky <xref:System.Windows.FrameworkElement>.  
  
 Následující tabulka uvádí vizuální vlastnosti zděděna z ovládacího prvku <xref:System.Windows.Controls.Control> třídy. Také to značí, zda ovládací prvek výchozí šablonu ovládacího prvku, použije se hodnota zděděné vlastnosti nebo musí být vázán šablony.  
  
|Vlastnost|Využití – metoda|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Dědičnost vlastnosti nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Dědičnost vlastnosti nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Dědičnost vlastnosti nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Dědičnost vlastnosti nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Dědičnost vlastnosti nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Vazba šablony|  
  
 V tabulce jsou uvedeny pouze visual vlastnosti zděděné od <xref:System.Windows.Controls.Control> třídy. Kromě vlastností uvedených v tabulce, mohou také dědit ovládacího prvku <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, a <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> vlastnosti z nadřazeného elementu framework.  
  
 Také pokud <xref:System.Windows.Controls.ContentPresenter> probíhá <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> bude automaticky svázán s <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti. Podobně <xref:System.Windows.Controls.ItemsPresenter> , který je v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ItemsControl> bude automaticky svázán s <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.ItemsPresenter> vlastnosti.  
  
 Následující příklad vytvoří dvě tlačítka, které používají <xref:System.Windows.Controls.ControlTemplate> definované v předchozím příkladu. V příkladu je nastavena <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, a <xref:System.Windows.Controls.Control.FontSize%2A> vlastnosti na každé tlačítko. Nastavení <xref:System.Windows.Controls.Control.Background%2A> vlastnost má efekt, protože je vázán v šabloně <xref:System.Windows.Controls.ControlTemplate>. I v případě, <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> vlastnosti nejsou šablony vázán, je nastavení má vliv, protože jejich hodnoty jsou zděděny.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 V předchozím příkladu vytvoří výstup, který se podobá následující obrázek.  
  
 ![Dvě tlačítka, jeden modrého tlačítka a jeden nachová. ](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dvě tlačítka s různými barvami pozadí  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Změna vzhledu ovládacího prvku v závislosti na stavu  
 Rozdíl mezi tlačítka s jeho výchozímu vzhledu a v předchozím příkladu je, že výchozí tlačítko mírně změní, když je v různých stavech. Například tlačítko výchozí vzhled změní při stisknutí tlačítka nebo když ukazatel myši je nad tlačítko. I když <xref:System.Windows.Controls.ControlTemplate> nezmění funkce ovládacího prvku, mění chování ovládacího prvku visual. Vizuální chování popisuje vzhled ovládacího prvku, až bude ve a jejich určitého stavu. Abyste pochopili rozdíl mezi visual chování ovládacího prvku a funkcí, podívejte se na příklad tlačítko. Funkce na tlačítko je zvýšit <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, když dojde ke kliknutí na, ale je změnit její vzhled, když je na kterou ukazuje nebo stisknutí tlačítka visual chování.  
  
 Použijete <xref:System.Windows.VisualState> objekty k určení vzhledu ovládacího prvku, pokud je v určitých stavu. A <xref:System.Windows.VisualState> obsahuje <xref:System.Windows.Media.Animation.Storyboard> , který změní vzhled elementů, které jsou v <xref:System.Windows.Controls.ControlTemplate>. Není potřeba psát jakýkoli kód, abychom způsobeny tím, že logiky ovládacího prvku pomocí změní stav <xref:System.Windows.VisualStateManager>. Když ovládací prvek přejde do stavu, která je zadána <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> vlastnost, <xref:System.Windows.Media.Animation.Storyboard> začíná. Při ukončení ovládací prvek stavu, <xref:System.Windows.Media.Animation.Storyboard> zastaví.  
  
 Následující příklad ukazuje <xref:System.Windows.VisualState> , který změní vzhled <xref:System.Windows.Controls.Button> při umístění ukazatele myši nad ním. <xref:System.Windows.Media.Animation.Storyboard> Změní barvu ohraničení tlačítka tak, že změníte barvu `BorderBrush`. Pokud odkazujete <xref:System.Windows.Controls.ControlTemplate> příklad na začátku tohoto tématu, které bude Vzpomeňte si, že `BorderBrush` je název <xref:System.Windows.Media.SolidColorBrush> přiřazené <xref:System.Windows.Controls.Border.Background%2A> z <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Ovládací prvek je zodpovědný za definování stavy jako součást jeho kontrakt ovládacího prvku, který je podrobně popsány v [přizpůsobení ostatní ovládací prvky Pochopením kontrakt ovládacího prvku](#customizing_other_controls_by_understanding_the_control_contract) dále v tomto tématu. V následující tabulce jsou uvedeny stavy, které jsou určené pro <xref:System.Windows.Controls.Button>.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad ovládací prvek.|  
|Stisknutí|CommonStates|Stisknutí ovládacího prvku.|  
|Zakázané|CommonStates|Ovládací prvek je zakázaný.|  
|Fokus|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
  
 <xref:System.Windows.Controls.Button> Definuje dvě skupiny stavů: `CommonStates` skupina obsahuje `Normal`, `MouseOver`, `Pressed`, a `Disabled` stavy. `FocusStates` Skupina obsahuje `Focused` a `Unfocused` stavy. Stavy ve stejné skupině stavů se vzájemně vylučují. Ovládací prvek, je vždy přesně jednoho stavu na skupinu. Například <xref:System.Windows.Controls.Button> i v případě, že ukazatel myši není nad ním, takže můžete mít fokus <xref:System.Windows.Controls.Button> v `Focused` stav může být v `MouseOver`, `Pressed`, nebo `Normal` stavu.  
  
 Přidáte <xref:System.Windows.VisualState> objektů <xref:System.Windows.VisualStateGroup> objekty. Přidáte <xref:System.Windows.VisualStateGroup> objektů <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost. Následující příklad definuje <xref:System.Windows.VisualState> objekty pro `Normal`, `MouseOver`, a `Pressed` stavy, které jsou všechny na `CommonStates` skupiny. <xref:System.Windows.VisualState.Name%2A> Jednotlivých <xref:System.Windows.VisualState> odpovídá názvu v předchozí tabulce. `Disabled` Stavu a stavu ve `FocusStates` skupiny jsou vynechány udržovat v příkladu krátký, ale jsou zahrnuty v celé příkladu na konci tohoto tématu.  
  
> [!NOTE]
>  Nezapomeňte nastavit <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost v kořenovém adresáři <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 V předchozím příkladu vytvoří výstup, který je podobný na následujících obrázcích.  
  
 ![Tlačítko se šablonou vlastního ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá šablonu vlastního ovládacího prvku v normálním stavu  
  
 ![Tlačítko se červené ohraničení. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá šablonu vlastního ovládacího prvku v myši nad stavu  
  
 ![Ohraničení je transparentní při stisknutí tlačítka. ](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Který používá šablonu vlastního ovládacího prvku ve stavu při stisknutí tlačítka  
  
 K vyhledání vizuálních stavů pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [– styly ovládacích prvků a šablon](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Určení chování ovládacího prvku, bude přecházet mezi stavy  
 V předchozím příkladu změní vzhled tlačítka také když na něj uživatel klikne, ale pokud stisknutí tlačítka pro celou sekundu uživatel není vidět její účinek. Ve výchozím nastavení trvá animace dojde k jedné sekundy. Vzhledem k tomu, že uživatelé budou pravděpodobně klikněte na tlačítko a uvolněte tlačítko v mnohem kratší dobu, vizuální zpětnou vazbu začnou platit, pokud jste nechali <xref:System.Windows.Controls.ControlTemplate> ve svém výchozím stavu.  
  
 Můžete zadat dobu, kterou trvá animace každý hladký přechod ovládacího prvku z jednoho stavu do jiného tak, že přidáte <xref:System.Windows.VisualTransition> objektů <xref:System.Windows.Controls.ControlTemplate>. Když vytvoříte <xref:System.Windows.VisualTransition>, můžete zadat jednu nebo víc z následujících akcí:  
  
-   Čas potřebný pro přechod mezi stavy, dojde k.  
  
-   Další změny vzhled ovládacího prvku, ke kterým dochází při přechodu.  
  
-   Které stavy <xref:System.Windows.VisualTransition> platí pro.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Určení doby trvání přechodu  
 Můžete určit, jak dlouho trvá přechod tak, že nastavíte <xref:System.Windows.VisualTransition.GeneratedDuration%2A> vlastnost. V předchozím příkladu má <xref:System.Windows.VisualState> , která určuje, že okraj tlačítka viditelný, při stisknutí tlačítka, ale animace trvá příliš dlouho být patrné, pokud je tlačítko rychle stisknutí a vydání. Můžete použít <xref:System.Windows.VisualTransition> určit dobu, trvá přechod do stavu při stisknutí ovládacího prvku. Následující příklad určuje, že ovládací prvek získá setiny sekundy přejde do stavu při stisknutí tlačítka.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Určení změn vzhled ovládacího prvku během přechodu  
 <xref:System.Windows.VisualTransition> Obsahuje <xref:System.Windows.Media.Animation.Storyboard> , který začíná, když ovládací prvek přechody mezi stavy. Například můžete určit, že některé animace nastane, pokud ovládací prvek se změní z `MouseOver` do stavu `Normal` stavu. Následující příklad vytvoří <xref:System.Windows.VisualTransition> , která určuje, že když uživatel přesune ukazatel myši mimo tlačítko, okraj tlačítka se změnami na modrou, pak na žlutou, pak na černou půl sekundy.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Určení, kdy použít VisualTransition  
 A <xref:System.Windows.VisualTransition> je možné omezit použití pouze určité stavy nebo jej lze použít pokaždé, když ovládací prvek přechodů mezi stavy. V předchozím příkladu <xref:System.Windows.VisualTransition> se použije, když se ovládací prvek dostane od `MouseOver` do stavu `Normal` stavu v příkladu, <xref:System.Windows.VisualTransition> se použije, když se ovládací prvek dostane do `Pressed` stavu. Když omezíte <xref:System.Windows.VisualTransition> platí tak, že nastavíte <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A> vlastnosti. Následující tabulka popisuje limity omezení od nejvíce omezující nejméně omezující.  
  
|Typ omezení|Hodnota z|Hodnota pro|  
|-------------------------|-------------------|-----------------|  
|V zadaném stavu do jiného zadaného stavu|Název <xref:System.Windows.VisualState>|Název <xref:System.Windows.VisualState>|  
|Z některému ze stavů do zadaného stavu|Nenastaveno|Název <xref:System.Windows.VisualState>|  
|V zadaném stavu k některému ze stavů|Název <xref:System.Windows.VisualState>|Nenastaveno|  
|Z některému ze stavů do jakéhokoli jiného stavu|Nenastaveno|Nenastaveno|  
  
 Můžete mít více <xref:System.Windows.VisualTransition> objekty v <xref:System.Windows.VisualStateGroup> , který se podívat do stejného stavu, ale je použijete v pořadí, ve kterém určuje v předchozí tabulce. V následujícím příkladu jsou dva <xref:System.Windows.VisualTransition> objekty. Když ovládací prvek změní z `Pressed` do stavu `MouseOver` stavu, <xref:System.Windows.VisualTransition> , který má obě <xref:System.Windows.VisualTransition.From%2A> a <xref:System.Windows.VisualTransition.To%2A> sada se používá. Když ovládací prvek přejde ze stavu, který není `Pressed` k `MouseOver` stavu stav se používá.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Má <xref:System.Windows.VisualStateGroup.Transitions%2A> vlastnost, která obsahuje <xref:System.Windows.VisualTransition> objekty, které se vztahují <xref:System.Windows.VisualState> objekty v <xref:System.Windows.VisualStateGroup>. Jako <xref:System.Windows.Controls.ControlTemplate> Autor, můžete libovolně k zahrnutí všech <xref:System.Windows.VisualTransition> chcete. Ale pokud <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A> vlastnosti jsou nastaveny na názvy států, které nejsou <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> se ignoruje.  
  
 Následující příklad ukazuje <xref:System.Windows.VisualStateGroup> pro `CommonStates`. V příkladu je definována <xref:System.Windows.VisualTransition> pro každé z následujících tlačítka přechody.  
  
-   Chcete `Pressed` stavu.  
  
-   Chcete `MouseOver` stavu.  
  
-   Z `Pressed` do stavu `MouseOver` stavu.  
  
-   Z `MouseOver` do stavu `Normal` stavu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Přizpůsobení dalších ovládacích prvků Pochopením kontrakt ovládacího prvku  
 Ovládací prvek, který se používá <xref:System.Windows.Controls.ControlTemplate> k určení jeho vizuální struktury (pomocí <xref:System.Windows.FrameworkElement> objekty) a visual chování (pomocí <xref:System.Windows.VisualState> objekty) používá model části ovládacího prvku. Mnoho ovládacích prvků, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 použijte tento model. Části, která <xref:System.Windows.Controls.ControlTemplate> Autor je potřeba mít na paměti, které se předávají prostřednictvím kontrakt ovládacího prvku. Při částí kontrakt ovládacího prvku porozumíte, můžete přizpůsobit vzhled libovolný ovládací prvek, který používá model části ovládacího prvku.  
  
 Kontrakt ovládacího prvku má tři prvky:  
  
-   Vizuální prvky, které používá logiky ovládacího prvku.  
  
-   Stavy ovládacího prvku a skupiny, do které patří každý stav.  
  
-   Veřejné vlastnosti, které ovlivňují vizuální ovládací prvek.  
  
### <a name="visual-elements-in-the-control-contract"></a>Vizuální prvky v kontrakt ovládacího prvku  
 Někdy logiky ovládacího prvku komunikuje <xref:System.Windows.FrameworkElement> , který je v <xref:System.Windows.Controls.ControlTemplate>. Například ovládací prvek může zpracovat událost jednoho z jeho prvků. Pokud se očekává, že ovládací prvek najít konkrétní <xref:System.Windows.FrameworkElement> v <xref:System.Windows.Controls.ControlTemplate>, je nutné sdělit <xref:System.Windows.Controls.ControlTemplate> Autor. Ovládací prvek používá <xref:System.Windows.TemplatePartAttribute> k předání typu prvku, který se očekává a co by měl být název elementu. <xref:System.Windows.Controls.Button> Nemá <xref:System.Windows.FrameworkElement> částí v jeho kontrakt ovládacího prvku, ale další ovládací prvky, jako <xref:System.Windows.Controls.ComboBox>, provést.  
  
 Následující příklad ukazuje <xref:System.Windows.TemplatePartAttribute> objekty, které jsou určeny na <xref:System.Windows.Controls.ComboBox> třídy. Logiku <xref:System.Windows.Controls.ComboBox> očekává <xref:System.Windows.Controls.TextBox> s názvem `PART_EditableTextBox` a <xref:System.Windows.Controls.Primitives.Popup> s názvem `PART_Popup` v jeho <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Následující příklad ukazuje je zjednodušená <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ComboBox> , který obsahuje prvky, které jsou určeny <xref:System.Windows.TemplatePartAttribute> objektů <xref:System.Windows.Controls.ComboBox> třídy.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stavy v kontrakt ovládacího prvku  
 Stavy ovládacího prvku jsou taky součástí kontrakt ovládacího prvku. Příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ukazuje, jak určit vzhled <xref:System.Windows.Controls.Button> v závislosti na stavech. Vytváření <xref:System.Windows.VisualState> pro každý zadaný stav a uveďte všechny <xref:System.Windows.VisualState> objekty tuto sdílenou složku <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> v <xref:System.Windows.VisualStateGroup>, jak je popsáno v [Změna vzhledu ovládacího prvku závisí na jeho stavu](#changing_the_appearance_of_a_control_depending_on_its_state) starší v tomto téma. Ovládací prvky třetích stran by měl určit stavy pomocí <xref:System.Windows.TemplateVisualStateAttribute>, což umožňuje návrhářské nástroje, jako je například Expression Blend, ke zveřejnění stavy ovládacího prvku pro vytváření šablon ovládacích prvků.  
  
 K vyhledání kontrakt ovládacího prvku pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [– styly ovládacích prvků a šablon](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Vlastnosti v kontrakt ovládacího prvku  
 Veřejné vlastnosti, které ovlivňují vizuálně ovládacího prvku jsou taky součástí kontrakt ovládacího prvku. Můžete nastavit tyto vlastnosti můžete změnit vzhled ovládacího prvku bez vytvoření nového <xref:System.Windows.Controls.ControlTemplate>. Můžete také použít [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) – rozšíření značek pro vazbu vlastnosti prvků, které jsou v <xref:System.Windows.Controls.ControlTemplate> na veřejné vlastnosti, které jsou definovány <xref:System.Windows.Controls.Button>.  
  
 Následující příklad ukazuje kontrakt ovládacího prvku tlačítka.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate>, často je nejjednodušší začít s existujícím <xref:System.Windows.Controls.ControlTemplate> a provádět změny. Můžete provést jednu z následujících akcí, chcete-li změnit existující <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Použití návrháře, jako je například Expression Blend, který poskytuje grafické uživatelské rozhraní pro vytváření šablon ovládacích prvků. Další informace najdete v tématu [práce se styly ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Získání výchozí <xref:System.Windows.Controls.ControlTemplate> a upravit ho. Najít výchozí šablony ovládacích prvků, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [výchozí WPF motivy](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> , která je popsána v tomto tématu.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
