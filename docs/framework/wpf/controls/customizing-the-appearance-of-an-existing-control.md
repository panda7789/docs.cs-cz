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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933721"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> Určuje vizuální strukturu a vizuální chování ovládacího prvku. Vzhled ovládacího prvku můžete přizpůsobit tak, že mu přiřadíte nový <xref:System.Windows.Controls.ControlTemplate>. Když vytvoříte <xref:System.Windows.Controls.ControlTemplate>, nahradíte vzhled existujícího ovládacího prvku beze změny jeho funkce. Například můžete nastavit, aby se tlačítka v aplikaci vyvolala místo výchozího čtvercového tvaru, ale tlačítko stále vyvolá <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost.  
  
 Toto téma vysvětluje různé části <xref:System.Windows.Controls.ControlTemplate>nástroje, ukazuje vytvoření jednoduchého <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>a vysvětluje, jak porozumět kontraktu ovládacího prvku ovládacího prvku, abyste mohli přizpůsobit jeho vzhled. Vzhledem k <xref:System.Windows.Controls.ControlTemplate> tomu, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vytvoříte v, můžete změnit vzhled ovládacího prvku bez psaní kódu. K vytvoření vlastních šablon ovládacích prvků můžete také použít návrháře, jako je například Microsoft Expression Blend. Toto téma ukazuje příklady v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , které přizpůsobují vzhled <xref:System.Windows.Controls.Button> a a uvádí kompletní příklad na konci tématu. Další informace o použití Blendu výrazů naleznete v tématu [stylování ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Následující ilustrace znázorňují <xref:System.Windows.Controls.Button> , který <xref:System.Windows.Controls.ControlTemplate> používá, který je vytvořen v tomto tématu.  
  
 ![Tlačítko s šablonou vlastního ovládacího prvku.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá vlastní šablonu ovládacího prvku  
  
 ![Tlačítko s červeným ohraničením.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá vlastní šablonu ovládacího prvku a má nad ním ukazatel myši  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte tomu, jak vytvořit a používat ovládací prvky a styly, jak je popsáno v [ovládacích prvcích](index.md). Koncepty popsané v tomto tématu se vztahují na prvky, které dědí z <xref:System.Windows.Controls.Control> třídy, s výjimkou <xref:System.Windows.Controls.UserControl>. Nelze použít <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.UserControl>pro.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Pokud byste měli vytvořit ControlTemplate  
 Ovládací prvky mají mnoho vlastností, <xref:System.Windows.Controls.Border.Background%2A>jako jsou, <xref:System.Windows.Controls.Control.Foreground%2A>a <xref:System.Windows.Controls.Control.FontFamily%2A>, které lze nastavit, chcete-li určit různé aspekty vzhledu ovládacího prvku, ale změny, které lze provést nastavením těchto vlastností, jsou omezeny. Můžete například nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na modrou a <xref:System.Windows.Controls.Control.FontStyle%2A> na kurzívu na <xref:System.Windows.Controls.CheckBox>.  
  
 Bez možnosti vytvářet nové <xref:System.Windows.Controls.ControlTemplate> ovládací prvky by měly mít všechny ovládací prvky v každé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikaci stejný vzhled, což by mělo omezit schopnost vytvořit aplikaci s vlastním vzhledem a chováním. Ve výchozím nastavení má <xref:System.Windows.Controls.CheckBox> každý z nich podobné charakteristiky. Například obsah <xref:System.Windows.Controls.CheckBox> je vždy napravo od indikátoru výběru a zaškrtnutí je vždy použito k označení <xref:System.Windows.Controls.CheckBox> toho, že je vybrána položka.  
  
 Vytvoříte <xref:System.Windows.Controls.ControlTemplate> , pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec toho, co nastavení dalších vlastností ovládacího prvku provede. V příkladu <xref:System.Windows.Controls.CheckBox>Předpokládejme, že chcete, aby obsah zaškrtávacího políčka byl nad indikátorem výběru a chcete <xref:System.Windows.Controls.CheckBox> , aby X označovala, že je vybrána položka. Tyto změny zadáte v <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>části.  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.CheckBox> , který používá výchozí <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Zaškrtávací políčko s výchozí šablonou ovládacího prvku.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaškrtávací políčko, které používá výchozí šablonu ovládacího prvku  
  
 Následující ilustrace znázorňuje <xref:System.Windows.Controls.CheckBox> , který používá vlastní <xref:System.Windows.Controls.ControlTemplate> obsah k <xref:System.Windows.Controls.CheckBox> umístění obsahu nad ukazatel <xref:System.Windows.Controls.CheckBox> výběru a při výběru je zobrazen X.  
  
 ![Zaškrtávací políčko s šablonou vlastního ovládacího prvku.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaškrtávací políčko, které používá vlastní šablonu ovládacího prvku  
  
 V této ukázce je poměrně složité, takže toto téma používá <xref:System.Windows.Controls.ControlTemplate> jednodušší příklad vytvoření pro <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Změna vizuální struktury ovládacího prvku  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je ovládací prvek často složených <xref:System.Windows.FrameworkElement> objektů. Když vytvoříte <xref:System.Windows.Controls.ControlTemplate>, zkombinujete <xref:System.Windows.FrameworkElement> objekty pro vytvoření jednoho ovládacího prvku. Musí mít pouze jeden <xref:System.Windows.FrameworkElement> kořenový element. <xref:System.Windows.Controls.ControlTemplate> Kořenový element obvykle obsahuje jiné <xref:System.Windows.FrameworkElement> objekty. Kombinace objektů tvoří vizuální strukturu ovládacího prvku.  
  
 Následující příklad vytvoří vlastní <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>pro. Vytvoří vizuální strukturu <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> V tomto příkladu se vzhled tlačítka nezmění, když na něj přesunete ukazatel myši nebo na něj kliknete. Změna vzhledu tlačítka, pokud je v jiném stavu, je popsána dále v tomto tématu.  
  
 V tomto příkladu se vizuální struktura skládá z následujících částí:  
  
- Název, který slouží jako kořen <xref:System.Windows.FrameworkElement>šablony. `RootElement` <xref:System.Windows.Controls.Border>  
  
- Objekt <xref:System.Windows.Controls.Grid> , který je `RootElement`podřízenou položkou.  
  
- A <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka. <xref:System.Windows.Controls.ContentPresenter> Umožňuje zobrazit libovolný typ objektu.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachování funkčnosti vlastností ovládacího prvku pomocí TemplateBinding  
 Když vytvoříte nový <xref:System.Windows.Controls.ControlTemplate>, můžete přesto chtít použít veřejné vlastnosti ke změně vzhledu ovládacího prvku. Rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) váže vlastnost prvku, který je v <xref:System.Windows.Controls.ControlTemplate> vlastnosti Public, která je definována ovládacím prvkem. Pokud používáte [TemplateBinding](../advanced/templatebinding-markup-extension.md), povolíte vlastnosti ovládacího prvku tak, aby sloužily jako parametry šablony. To znamená, že když je nastavena vlastnost ovládacího prvku, je tato hodnota předána prvku, který má [TemplateBinding](../advanced/templatebinding-markup-extension.md) .  
  
 Následující příklad opakuje část předchozího příkladu, který používá rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) k vázání vlastností prvků, které jsou ve <xref:System.Windows.Controls.ControlTemplate> vlastnostech Public, které jsou definovány tlačítkem.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 V tomto příkladu <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> má vlastnost navázánou na <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>šablonu. Vzhledem <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> k tomu, že je vázaný na šablonu, můžete vytvořit více tlačítek <xref:System.Windows.Controls.ControlTemplate> , která používají <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> stejnou hodnotu, a nastavit na každé tlačítko jiné hodnoty. Pokud <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> nebyla vytvořena vazba šablony k vlastnosti prvku <xref:System.Windows.Controls.ControlTemplate>v, nastavení <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> tlačítka by neměla mít žádný vliv na vzhled tlačítka.  
  
 Všimněte si, že názvy dvou vlastností nemusejí být identické. V předchozím příkladu <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> je vlastnost <xref:System.Windows.Controls.Button> šablony svázána <xref:System.Windows.Controls.ContentPresenter>s <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> vlastností třídy. Tím umožníte, aby byl obsah tlačítka umístěn vodorovně. <xref:System.Windows.Controls.ContentPresenter>neobsahuje vlastnost s názvem `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> může být svázána s <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Když šablonu svážete s vlastností, ujistěte se, že vlastnosti target a Source jsou stejného typu.  
  
 <xref:System.Windows.Controls.Control> Třída definuje několik vlastností, které musí být použity šablonou ovládacího prvku, aby měly vliv na ovládací prvek, když jsou nastaveny. Způsob, <xref:System.Windows.Controls.ControlTemplate> jakým tato vlastnost používá, závisí na vlastnosti. Vlastnost <xref:System.Windows.Controls.ControlTemplate> musí používat v jednom z následujících způsobů:  
  
- Prvek v <xref:System.Windows.Controls.ControlTemplate> šabloně se váže k vlastnosti.  
  
- Element ve <xref:System.Windows.Controls.ControlTemplate> dědí vlastnost z nadřazené <xref:System.Windows.FrameworkElement>třídy.  
  
 V následující tabulce jsou uvedeny vlastnosti vizuálu zděděné ovládacím prvkem z <xref:System.Windows.Controls.Control> třídy. Označuje také, zda výchozí šablona ovládacího prvku ovládacího prvku používá zděděnou hodnotu vlastnosti nebo zda musí být vázaná na šablonu.  
  
|Vlastnost|Metoda použití|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Dědičnost vlastností nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Dědičnost vlastností nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Dědičnost vlastností nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Dědičnost vlastností nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Dědičnost vlastností nebo vazba šablony|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Vazba šablony|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Vazba šablony|  
  
 V tabulce jsou uvedeny pouze vlastnosti vizuálu zděděné z <xref:System.Windows.Controls.Control> třídy. Kromě vlastností uvedených v tabulce může ovládací prvek také dědit <xref:System.Windows.FrameworkElement.DataContext%2A>vlastnosti, <xref:System.Windows.FrameworkElement.Language%2A>a <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> z nadřazeného prvku rozhraní.  
  
 Kromě toho, pokud <xref:System.Windows.Controls.ContentPresenter> je <xref:System.Windows.Controls.ControlTemplate> v <xref:System.Windows.Controls.ContentControl>,, <xref:System.Windows.Controls.ContentPresenter> se automaticky vytvoří vazba s <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnostmi a <xref:System.Windows.Controls.ContentControl.Content%2A> . Podobně <xref:System.Windows.Controls.ItemsPresenter> ,,,, který je <xref:System.Windows.Controls.ControlTemplate> v z <xref:System.Windows.Controls.ItemsControl> , bude automaticky svázán s <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnostmi a <xref:System.Windows.Controls.ItemsPresenter> .  
  
 Následující příklad vytvoří dvě tlačítka, která používají <xref:System.Windows.Controls.ControlTemplate> definované v předchozím příkladu. Příklad nastaví <xref:System.Windows.Controls.Control.Background%2A>vlastnosti, <xref:System.Windows.Controls.Control.Foreground%2A>a <xref:System.Windows.Controls.Control.FontSize%2A> na každém tlačítku. Nastavení vlastnosti má vliv, protože se jedná o šablonu svázanou <xref:System.Windows.Controls.ControlTemplate>v. <xref:System.Windows.Controls.Control.Background%2A> I když vlastnosti <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> nejsou vázané na šablonu, jejich nastavení má vliv, protože jejich hodnoty jsou zděděné.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Předchozí příklad vytvoří výstup podobný následujícímu obrázku.  
  
 ![Dvě tlačítka, jedna modrá a jedna fialová.](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dvě tlačítka s různými barvami pozadí  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Změna vzhledu ovládacího prvku v závislosti na jeho stavu  
 Rozdíl mezi tlačítkem s výchozím zobrazením a tlačítkem v předchozím příkladu je, že výchozí tlačítko se při různých stavech mírně mění. Například vzhled výchozího tlačítka se změní, když je stisknuto tlačítko, nebo když je ukazatel myši nad tlačítkem. <xref:System.Windows.Controls.ControlTemplate> Ačkoliv nemění funkčnost ovládacího prvku, změní vizuální chování ovládacího prvku. Vizuální chování popisuje vzhled ovládacího prvku, když je v určitém stavu. Chcete-li pochopit rozdíl mezi funkcí a vizuální chování ovládacího prvku, zvažte příklad tlačítka. Funkce tlačítka je vyvolat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost při kliknutí, ale vizuální chování tlačítka je změnit jeho vzhled, pokud je odkazováno nebo stisknuto.  
  
 Objekty lze <xref:System.Windows.VisualState> použít k určení vzhledu ovládacího prvku, pokud je v určitém stavu. Obsahuje objekt <xref:System.Windows.Media.Animation.Storyboard> , který mění vzhled <xref:System.Windows.Controls.ControlTemplate>prvků, které jsou v. <xref:System.Windows.VisualState> Nemusíte psát žádný kód, aby k tomu došlo, protože logika ovládacího prvku mění stav pomocí <xref:System.Windows.VisualStateManager>. Když ovládací prvek vstoupí do stavu, který je určen <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> vlastností <xref:System.Windows.Media.Animation.Storyboard> , začne. Když ovládací prvek ukončí stav, zastaví se <xref:System.Windows.Media.Animation.Storyboard> .  
  
 Následující příklad ukazuje <xref:System.Windows.VisualState> , že se změní vzhled <xref:System.Windows.Controls.Button> , když je ukazatel myši nad ním. Změní barvu ohraničení tlačítka změnou barvy `BorderBrush`. <xref:System.Windows.Media.Animation.Storyboard> Pokud <xref:System.Windows.Controls.ControlTemplate> odkazujete na příklad na začátku tohoto tématu, budete si vypomenout, `BorderBrush` že <xref:System.Windows.Media.SolidColorBrush> se jedná o název, který je přiřazený ke službě <xref:System.Windows.Controls.Border.Background%2A>. <xref:System.Windows.Controls.Border>  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Tento ovládací prvek zodpovídá za definování států v rámci své kontrolní smlouvy, která je podrobněji popsána v tématu [přizpůsobení dalších ovládacích prvků pomocí porozumění kontraktu řízení](#customizing_other_controls_by_understanding_the_control_contract) dále v tomto tématu. V následující tabulce jsou uvedeny stavy, které jsou určeny pro <xref:System.Windows.Controls.Button>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|  
|Stisknutí|CommonStates|Ovládací prvek se stiskne.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázán.|  
|Zaměřil|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
  
 `CommonStates` `Normal` Definujedvě`Disabled` skupiny stavů `MouseOver` :`Pressed`skupina obsahuje stavy,, a. <xref:System.Windows.Controls.Button> Skupina obsahuje stavy`Unfocused` a `Focused`. `FocusStates` Stavy ve stejné skupině stavů se vzájemně vylučují. Ovládací prvek je vždy v přesně jednom stavu na skupinu. <xref:System.Windows.Controls.Button> Například `Pressed`může mít fokus i `Focused` <xref:System.Windows.Controls.Button> v případě, že ukazatel myši není nad ním, takže ve stavu může být `MouseOver`ve stavu, nebo `Normal` .  
  
 Přidáte <xref:System.Windows.VisualState> objekty do <xref:System.Windows.VisualStateGroup> objektů. Přidáte <xref:System.Windows.VisualStateGroup> objekty<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> do připojené vlastnosti. Následující <xref:System.Windows.VisualState> příklad definuje objekty `MouseOver` `Normal`pro stavy, `Pressed` a,kteréjsouveskupiněvšechny.`CommonStates` <xref:System.Windows.VisualState.Name%2A> U každého<xref:System.Windows.VisualState> odpovídá názvu v předchozí tabulce. Stav a stavy `FocusStates` ve skupině jsou vynechány, aby byl příklad krátký, ale jsou obsaženy v celém příkladu na konci tohoto tématu. `Disabled`  
  
> [!NOTE]
> Ujistěte se, že jste <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> nastavili připojenou <xref:System.Windows.FrameworkElement> vlastnost v <xref:System.Windows.Controls.ControlTemplate>kořenu.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Předchozí příklad vytvoří výstup podobný následujícímu obrázku.  
  
 ![Tlačítko s šablonou vlastního ovládacího prvku.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Tlačítko, které používá vlastní šablonu ovládacího prvku v normálním stavu  
  
 ![Tlačítko s červeným ohraničením.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Tlačítko, které používá vlastní šablonu ovládacího prvku ve stavu přetažení myší  
  
 ![Ohraničení je transparentní pro tlačítko stisknuté.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Tlačítko, které používá vlastní šablonu ovládacího prvku ve stisknutém stavu  
  
 Chcete-li najít vizuální stavy pro ovládací prvky, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jsou součástí nástroje, viz téma [styly a šablony ovládacích prvků](control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Určení chování ovládacího prvku při přechodu mezi stavy  
 V předchozím příkladu se vzhled tlačítka také změní, když na něj uživatel klikne, ale pokud se tlačítko nestiskne po celou sekundu, uživatel se neprojeví. Ve výchozím nastavení trvá animace jedna sekunda. Vzhledem k tomu, že uživatelé budou mít pravděpodobně tlačítko a uvolní tlačítko v mnohem kratší dobu, nebude vaše vizuální vazba účinná, pokud <xref:System.Windows.Controls.ControlTemplate> ve svém výchozím stavu odejdete.  
  
 Můžete zadat dobu, po kterou bude trvat animace pro plynulé přesunutí ovládacího prvku z jednoho stavu do druhého přidáním <xref:System.Windows.VisualTransition> objektů <xref:System.Windows.Controls.ControlTemplate>do objektu. Při vytváření <xref:System.Windows.VisualTransition>zadejte jednu nebo více z následujících možností:  
  
- Čas potřebný k přechodu mezi stavy, které mají být provedeny.  
  
- Další změny vzhledu ovládacího prvku, ke kterým dojde v době přechodu.  
  
- Který uvádí, <xref:System.Windows.VisualTransition> že se používá.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Určení doby trvání přechodu  
 Nastavením <xref:System.Windows.VisualTransition.GeneratedDuration%2A> vlastnosti můžete určit, jak dlouho trvá přechod. Předchozí příklad má hodnotu <xref:System.Windows.VisualState> , která určuje, že ohraničení tlačítka bude při stisknutí tlačítka transparentní, ale pokud se tlačítko rychle stiskne a uvolní, animace trvá příliš dlouho. Můžete použít <xref:System.Windows.VisualTransition> k určení doby, po kterou má ovládací prvek přejít do stisknutého stavu. Následující příklad určuje, že ovládací prvek převezme jedno setiny sekundy, aby přešl do stavu stisknuto.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Určení změn vzhledu ovládacího prvku během přechodu  
 <xref:System.Windows.VisualTransition> Obsahuje,kterýzačínápřipřechodu<xref:System.Windows.Media.Animation.Storyboard> ovládacího prvku mezi stavy. Můžete například určit, že k určité animaci dojde, když ovládací prvek přejde ze `MouseOver` stavu `Normal` do stavu. Následující příklad vytvoří <xref:System.Windows.VisualTransition> , který určuje, že když uživatel přesune ukazatel myši na tlačítko, změní se ohraničení tlačítka na modroo a potom na žlutou, a to na černou během 1,5 sekund.  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Určení, kdy se používá VisualTransition  
 <xref:System.Windows.VisualTransition> Může být omezeno na použití pouze v určitých stavech nebo může být použito kdykoli při přechodu ovládacího prvku mezi stavy. <xref:System.Windows.VisualTransition> V předchozím příkladu je použita v případě, kdy ovládací prvek přejde `Normal` `MouseOver` ze stavu do stavu <xref:System.Windows.VisualTransition> ; v příkladu je použita, když ovládací prvek přejde do `Pressed` stavu. Omezením, kdy <xref:System.Windows.VisualTransition> se používá, můžete omezit <xref:System.Windows.VisualTransition.To%2A> nastavením <xref:System.Windows.VisualTransition.From%2A> vlastností a. V následující tabulce jsou popsány úrovně omezení od nejvíce omezující po nejméně omezující.  
  
|Typ omezení|Hodnota z|Hodnota do|  
|-------------------------|-------------------|-----------------|  
|Z určeného stavu do jiného zadaného stavu|Název<xref:System.Windows.VisualState>|Název<xref:System.Windows.VisualState>|  
|Ze všech stavů do zadaného stavu|Nenastaveno|Název<xref:System.Windows.VisualState>|  
|Z určeného stavu do libovolného stavu|Název<xref:System.Windows.VisualState>|Nenastaveno|  
|Z libovolného stavu do jakéhokoli jiného stavu|Nenastaveno|Nenastaveno|  
  
 Můžete mít více <xref:System.Windows.VisualTransition> objektů <xref:System.Windows.VisualStateGroup> v objektu, které odkazují na stejný stav, ale budou použity v pořadí, v jakém má předchozí tabulka. V následujícím příkladu jsou dva <xref:System.Windows.VisualTransition> objekty. Když ovládací prvek přechází ze `Pressed` stavu `MouseOver` do stavu, <xref:System.Windows.VisualTransition> je použita sada, která <xref:System.Windows.VisualTransition.From%2A> obsahuje <xref:System.Windows.VisualTransition.To%2A> obě i sady. Když ovládací prvek přejde ze stavu, který `Pressed` není `MouseOver` do stavu, je použit druhý stav.  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualState> Mávlastnost,<xref:System.Windows.VisualStateGroup>která obsahuje <xref:System.Windows.VisualTransition> objekty, které se vztahují na objekty v. <xref:System.Windows.VisualStateGroup.Transitions%2A> <xref:System.Windows.VisualStateGroup> Jako autor můžete zahrnout všechny <xref:System.Windows.VisualTransition> požadované. <xref:System.Windows.Controls.ControlTemplate> Nicméně pokud <xref:System.Windows.VisualTransition.To%2A> jsou vlastnosti a <xref:System.Windows.VisualTransition.From%2A> nastaveny na názvy stavů <xref:System.Windows.VisualStateGroup>, které nejsou v, <xref:System.Windows.VisualTransition> je ignorována.  
  
 Následující příklad ukazuje <xref:System.Windows.VisualStateGroup> `CommonStates`pro. Příklad definuje <xref:System.Windows.VisualTransition> pro každé z následujících přechodů tlačítek.  
  
- `Pressed` Do stavu.  
  
- `MouseOver` Do stavu.  
  
- `Pressed` Ze stavu`MouseOver` do stavu.  
  
- `MouseOver` Ze stavu`Normal` do stavu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Přizpůsobení dalších ovládacích prvků pomocí porozumění kontraktu řízení  
 Ovládací prvek, který používá <xref:System.Windows.Controls.ControlTemplate> k určení jeho vizuální struktury ( <xref:System.Windows.FrameworkElement> pomocí objektů) a <xref:System.Windows.VisualState> vizuální chování (pomocí objektů), používá model řízení částí. Tento model používá mnoho ovládacích prvků, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou součástí 4. Části, o kterých <xref:System.Windows.Controls.ControlTemplate> autor potřebuje vědět, se sdělují prostřednictvím smlouvy o řízení. Pokud rozumíte částem kontraktu ovládacího prvku, můžete přizpůsobit vzhled libovolného ovládacího prvku, který používá model ovládacího prvku součásti.  
  
 Kontrakt ovládacího prvku má tři prvky:  
  
- Vizuální prvky, které logika ovládacího prvku používá.  
  
- Stavy ovládacího prvku a skupiny, do kterých každý stav patří.  
  
- Veřejné vlastnosti, které vizuálně ovlivňují ovládací prvek.  
  
### <a name="visual-elements-in-the-control-contract"></a>Vizuální prvky v kontraktu řízení  
 V některých případech logika ovládacího prvku komunikuje s objektem <xref:System.Windows.FrameworkElement> , který je v. <xref:System.Windows.Controls.ControlTemplate> Například ovládací prvek může zpracovat událost jednoho z jeho prvků. Když ovládací prvek očekává <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>, že najde konkrétní informace v, musí <xref:System.Windows.Controls.ControlTemplate> předat tyto informace autorovi. Ovládací prvek používá <xref:System.Windows.TemplatePartAttribute> pro vyjádření typu prvku, který je očekáván a jaký má název elementu. Neobsahuje části v rámci kontraktu řízení, ale jiné ovládací prvky, jako je <xref:System.Windows.Controls.ComboBox>například. <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.Button>  
  
 Následující příklad ukazuje <xref:System.Windows.TemplatePartAttribute> objekty, které jsou zadány <xref:System.Windows.Controls.ComboBox> ve třídě. <xref:System.Windows.Controls.ComboBox> Logika očekává, že se ve svém <xref:System.Windows.Controls.TextBox> `PART_Popup` `PART_EditableTextBox` <xref:System.Windows.Controls.Primitives.Popup> polinajdepojmenovanéapojmenované<xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Následující příklad ukazuje zjednodušenou <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> pro, který obsahuje prvky <xref:System.Windows.TemplatePartAttribute> , které jsou určeny objekty ve <xref:System.Windows.Controls.ComboBox> třídě.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stavy v rámci kontraktu řízení  
 Stavy ovládacího prvku jsou také součástí kontraktu ovládacího prvku. Příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> pro pro ukazuje, jak <xref:System.Windows.Controls.Button> určit vzhled v závislosti na jeho stavech. Vytvoříte <xref:System.Windows.VisualState> pro každý zadaný stav a zadáte všechny <xref:System.Windows.VisualState> objekty <xref:System.Windows.VisualStateGroup>, které sdílí a <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> , jak je popsáno v části [Změna vzhledu ovládacího prvku v závislosti na jeho stavu](#changing_the_appearance_of_a_control_depending_on_its_state) dříve v tomto tématu. Ovládací prvky třetích stran by měly určovat stavy pomocí <xref:System.Windows.TemplateVisualStateAttribute>nástroje, který umožňuje nástrojům návrháře, jako je například Blend Expressions, vystavovat stavy ovládacích prvků pro vytváření šablon ovládacích prvků.  
  
 Chcete-li najít kontrakt řízení pro ovládací prvky, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jsou součástí nástroje, viz téma [styly a šablony ovládacích prvků](control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Vlastnosti v kontraktu řízení  
 Veřejné vlastnosti, které vizuálně ovlivňují ovládací prvek, jsou zahrnuty i v rámci kontraktu řízení. Nastavením těchto vlastností lze změnit vzhled ovládacího prvku bez vytvoření nového <xref:System.Windows.Controls.ControlTemplate>. Můžete také použít rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) k vázání vlastností prvků, které jsou ve <xref:System.Windows.Controls.ControlTemplate> vlastnostech veřejné vlastnosti, které jsou definovány v. <xref:System.Windows.Controls.Button>  
  
 Následující příklad ukazuje kontrakt ovládacího prvku pro tlačítko.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate>je často nejjednodušší začít s existujícím <xref:System.Windows.Controls.ControlTemplate> a provádět v něm změny. Chcete-li změnit existující <xref:System.Windows.Controls.ControlTemplate>, můžete provést jednu z následujících akcí:  
  
- Použijte návrháře, jako je například výraz Blend, který poskytuje grafické uživatelské rozhraní pro vytváření šablon ovládacích prvků. Další informace naleznete v tématu [stylování ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
- Získejte výchozí hodnotu <xref:System.Windows.Controls.ControlTemplate> a upravte ji. Chcete-li najít výchozí šablony ovládacích prvků, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jsou součástí nástroje, přečtěte si téma [výchozí motivy WPF](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> popis, který je popsán v tomto tématu.  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
