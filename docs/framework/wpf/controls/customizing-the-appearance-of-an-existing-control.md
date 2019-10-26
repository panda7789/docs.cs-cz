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
ms.openlocfilehash: 0c79ba3dd42f2e65eb241409946e921577ced5f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920054"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> určuje vizuální strukturu a vizuální chování ovládacího prvku. Vzhled ovládacího prvku můžete přizpůsobit tak, že mu udělíte novou <xref:System.Windows.Controls.ControlTemplate>. Při vytváření <xref:System.Windows.Controls.ControlTemplate>nahradíte vzhled existujícího ovládacího prvku beze změny jeho funkce. Například můžete nastavit, aby se tlačítka v aplikaci vyvolala místo výchozího čtvercového tvaru, ale tlačítko bude stále zvyšovat událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 Toto téma vysvětluje různé části <xref:System.Windows.Controls.ControlTemplate>, ukazuje vytvoření jednoduchého <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>a vysvětluje, jak porozumět kontraktu ovládacího prvku ovládacího prvku, abyste mohli přizpůsobit jeho vzhled. Vzhledem k tomu, že vytvoříte <xref:System.Windows.Controls.ControlTemplate> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete změnit vzhled ovládacího prvku bez psaní kódu. K vytvoření vlastních šablon ovládacích prvků můžete použít také návrháře, například Blend pro Visual Studio. V tomto tématu jsou uvedeny příklady [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], které přizpůsobují vzhled <xref:System.Windows.Controls.Button> a uvádějí kompletní příklad na konci tématu. Další informace o použití Blend pro Visual Studio naleznete v tématu [stylování ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).

 Následující ilustrace znázorňují <xref:System.Windows.Controls.Button>, která používá <xref:System.Windows.Controls.ControlTemplate> vytvořené v tomto tématu.

 ![Tlačítko s šablonou vlastního ovládacího prvku.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Tlačítko, které používá vlastní šablonu ovládacího prvku

 ![Tlačítko s červeným ohraničením.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Tlačítko, které používá vlastní šablonu ovládacího prvku a má nad ním ukazatel myši

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky
 Toto téma předpokládá, že rozumíte tomu, jak vytvořit a používat ovládací prvky a styly, jak je popsáno v [ovládacích prvcích](index.md). Koncepty popsané v tomto tématu se vztahují na prvky, které dědí z třídy <xref:System.Windows.Controls.Control>, s výjimkou <xref:System.Windows.Controls.UserControl>. Nemůžete použít <xref:System.Windows.Controls.ControlTemplate> na <xref:System.Windows.Controls.UserControl>.

<a name="when_you_should_create_a_controltemplate"></a>
## <a name="when-you-should-create-a-controltemplate"></a>Pokud byste měli vytvořit ControlTemplate
 Ovládací prvky mají mnoho vlastností, například <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>a <xref:System.Windows.Controls.Control.FontFamily%2A>, které lze nastavit tak, aby určovaly různé aspekty vzhledu ovládacího prvku, ale změny, které lze provést nastavením těchto vlastností, jsou omezeny. Například můžete nastavit vlastnost <xref:System.Windows.Controls.Control.Foreground%2A> na modrou a <xref:System.Windows.Controls.Control.FontStyle%2A> na kurzívu na <xref:System.Windows.Controls.CheckBox>.

 Bez možnosti vytvářet nové <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvky by měly mít všechny ovládací prvky v každé aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]stejný vzhled, který by omezil možnost vytvářet aplikace s vlastním vzhledem a chováním. Ve výchozím nastavení má každá <xref:System.Windows.Controls.CheckBox> podobné charakteristiky. Například obsah <xref:System.Windows.Controls.CheckBox> je vždy napravo od indikátoru výběru a zaškrtnutí je vždy použito k označení toho, že <xref:System.Windows.Controls.CheckBox> je vybrána.

 Vytvoříte <xref:System.Windows.Controls.ControlTemplate>, pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec toho, co nastavení dalších vlastností ovládacího prvku provede. V příkladu <xref:System.Windows.Controls.CheckBox>Předpokládejme, že chcete, aby obsah zaškrtávacího políčka byl nad indikátorem výběru a chcete, aby X označovala, že je vybrána <xref:System.Windows.Controls.CheckBox>. Tyto změny zadáte v <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>.

 Následující obrázek ukazuje <xref:System.Windows.Controls.CheckBox>, který používá výchozí <xref:System.Windows.Controls.ControlTemplate>.

 ![Zaškrtávací políčko s výchozí šablonou ovládacího prvku.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Zaškrtávací políčko, které používá výchozí šablonu ovládacího prvku

 Následující ilustrace znázorňuje <xref:System.Windows.Controls.CheckBox>, která používá vlastní <xref:System.Windows.Controls.ControlTemplate> k umístění obsahu <xref:System.Windows.Controls.CheckBox> nad indikátor výběru a při výběru <xref:System.Windows.Controls.CheckBox> zobrazí hodnotu X.

 ![Zaškrtávací políčko s šablonou vlastního ovládacího prvku.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Zaškrtávací políčko, které používá vlastní šablonu ovládacího prvku

 <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.CheckBox> v této ukázce je poměrně složitá, takže toto téma používá jednodušší příklad vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.

<a name="changing_the_visual_structure_of_a_control"></a>
## <a name="changing-the-visual-structure-of-a-control"></a>Změna vizuální struktury ovládacího prvku
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je ovládací prvek často složeným <xref:System.Windows.FrameworkElement>m objektům. Při vytváření <xref:System.Windows.Controls.ControlTemplate>kombinujete <xref:System.Windows.FrameworkElement> objektů pro sestavení jednoho ovládacího prvku. <xref:System.Windows.Controls.ControlTemplate> musí mít pouze jeden <xref:System.Windows.FrameworkElement> jako svůj kořenový prvek. Kořenový element obvykle obsahuje další objekty <xref:System.Windows.FrameworkElement>. Kombinace objektů tvoří vizuální strukturu ovládacího prvku.

 Následující příklad vytvoří vlastní <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> vytvoří vizuální strukturu <xref:System.Windows.Controls.Button>. V tomto příkladu se vzhled tlačítka nezmění, když na něj přesunete ukazatel myši nebo na něj kliknete. Změna vzhledu tlačítka, pokud je v jiném stavu, je popsána dále v tomto tématu.

 V tomto příkladu se vizuální struktura skládá z následujících částí:

- <xref:System.Windows.Controls.Border> s názvem `RootElement`, který slouží jako kořenový <xref:System.Windows.FrameworkElement>šablony.

- <xref:System.Windows.Controls.Grid>, která je podřízenou položkou `RootElement`.

- <xref:System.Windows.Controls.ContentPresenter>, který zobrazuje obsah tlačítka <xref:System.Windows.Controls.ContentPresenter> povoluje zobrazení libovolného typu objektu.

 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]

### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachování funkčnosti vlastností ovládacího prvku pomocí TemplateBinding
 Když vytvoříte novou <xref:System.Windows.Controls.ControlTemplate>, můžete přesto chtít použít veřejné vlastnosti ke změně vzhledu ovládacího prvku. Rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) váže vlastnost prvku, který je v <xref:System.Windows.Controls.ControlTemplate> k veřejné vlastnosti, která je definována ovládacím prvkem. Pokud používáte [TemplateBinding](../advanced/templatebinding-markup-extension.md), povolíte vlastnosti ovládacího prvku tak, aby sloužily jako parametry šablony. To znamená, že když je nastavena vlastnost ovládacího prvku, je tato hodnota předána prvku, který má [TemplateBinding](../advanced/templatebinding-markup-extension.md) .

 Následující příklad opakuje část předchozího příkladu, který používá rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) k vázání vlastností prvků, které jsou v <xref:System.Windows.Controls.ControlTemplate> veřejných vlastností, které jsou definovány tlačítkem.

 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]

 V tomto příkladu má <xref:System.Windows.Controls.Grid> jeho šablonu <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost je svázána s <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Vzhledem k tomu, že <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> je vázaná na šablonu, můžete vytvořit více tlačítek, která používají stejný <xref:System.Windows.Controls.ControlTemplate> a nastavit <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> na různé hodnoty na každém tlačítku. Pokud <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> nebyla svázaná s vlastností elementu v <xref:System.Windows.Controls.ControlTemplate>, nastavení <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> tlačítka nebude mít žádný vliv na vzhled tlačítka.

 Všimněte si, že názvy dvou vlastností nemusejí být identické. V předchozím příkladu je vlastnost <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Button>a šablona vázaná na vlastnost <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.ContentPresenter>. Tím umožníte, aby byl obsah tlačítka umístěn vodorovně. <xref:System.Windows.Controls.ContentPresenter> nemá vlastnost s názvem `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> mohou být vázány na <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Když šablonu svážete s vlastností, ujistěte se, že vlastnosti target a Source jsou stejného typu.

 Třída <xref:System.Windows.Controls.Control> definuje několik vlastností, které musí být použity šablonou ovládacího prvku, aby měly vliv na ovládací prvek, když jsou nastaveny. Způsob, jakým <xref:System.Windows.Controls.ControlTemplate> používá vlastnost závisí na vlastnosti. <xref:System.Windows.Controls.ControlTemplate> musí použít vlastnost jedním z následujících způsobů:

- Prvek v šabloně <xref:System.Windows.Controls.ControlTemplate> se váže k vlastnosti.

- Prvek ve <xref:System.Windows.Controls.ControlTemplate> dědí vlastnost z nadřazené <xref:System.Windows.FrameworkElement>.

 V následující tabulce jsou uvedeny vlastnosti vizuálu zděděné ovládacím prvkem z třídy <xref:System.Windows.Controls.Control>. Označuje také, zda výchozí šablona ovládacího prvku ovládacího prvku používá zděděnou hodnotu vlastnosti nebo zda musí být vázaná na šablonu.

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

 V tabulce jsou uvedeny pouze vlastnosti vizuálu zděděné z <xref:System.Windows.Controls.Control> třídy. Kromě vlastností uvedených v tabulce může ovládací prvek také dědit vlastnosti <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>a <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> z nadřazeného prvku rozhraní.

 Pokud je <xref:System.Windows.Controls.ContentPresenter> v <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> automaticky vytvoří vazby na <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnosti. Podobně <xref:System.Windows.Controls.ItemsPresenter> <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> automaticky vytvoří vazby na <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.ItemsPresenter> vlastnosti.

 Následující příklad vytvoří dvě tlačítka, která používají <xref:System.Windows.Controls.ControlTemplate> definované v předchozím příkladu. V příkladu se pro každé tlačítko nastaví vlastnosti <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>a <xref:System.Windows.Controls.Control.FontSize%2A>. Nastavení vlastnosti <xref:System.Windows.Controls.Control.Background%2A> má efekt, protože se jedná o šablonu svázanou v <xref:System.Windows.Controls.ControlTemplate>. I když vlastnosti <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> nejsou vázané na šablonu, jejich nastavení má vliv, protože jejich hodnoty jsou zděděné.

 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]

 Předchozí příklad vytvoří výstup podobný následujícímu obrázku.

 ![Dvě tlačítka, jedna modrá a jedna fialová.](./media/ndp-buttontwo.png "NDP_ButtonTwo")
Dvě tlačítka s různými barvami pozadí

<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Změna vzhledu ovládacího prvku v závislosti na jeho stavu
 Rozdíl mezi tlačítkem s výchozím zobrazením a tlačítkem v předchozím příkladu je, že výchozí tlačítko se při různých stavech mírně mění. Například vzhled výchozího tlačítka se změní, když je stisknuto tlačítko, nebo když je ukazatel myši nad tlačítkem. I když <xref:System.Windows.Controls.ControlTemplate> nemění funkčnost ovládacího prvku, změní vizuální chování ovládacího prvku. Vizuální chování popisuje vzhled ovládacího prvku, když je v určitém stavu. Chcete-li pochopit rozdíl mezi funkcí a vizuální chování ovládacího prvku, zvažte příklad tlačítka. Funkce tlačítka je vyvolat událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, když se na ni klikne, ale vizuální chování tlačítka má změnit jeho vzhled, když je na něj odkazováno nebo stisknuto.

 Pomocí <xref:System.Windows.VisualState> objektů určíte vzhled ovládacího prvku, pokud je v určitém stavu. <xref:System.Windows.VisualState> obsahuje <xref:System.Windows.Media.Animation.Storyboard>, který mění vzhled prvků, které jsou v <xref:System.Windows.Controls.ControlTemplate>. Nemusíte psát žádný kód, aby k tomu došlo, protože logika ovládacího prvku mění stav pomocí <xref:System.Windows.VisualStateManager>. Když ovládací prvek vstoupí do stavu, který je určen vlastností <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>, zahájí <xref:System.Windows.Media.Animation.Storyboard>. Když ovládací prvek ukončí stav, <xref:System.Windows.Media.Animation.Storyboard> se zastaví.

 Následující příklad ukazuje <xref:System.Windows.VisualState>, který změní vzhled <xref:System.Windows.Controls.Button>, když je nad ním ukazatel myši. <xref:System.Windows.Media.Animation.Storyboard> změní barvu ohraničení tlačítka změnou barvy `BorderBrush`. Pokud odkazujete na <xref:System.Windows.Controls.ControlTemplate> příklad na začátku tohoto tématu, odvoláte ho `BorderBrush` je název <xref:System.Windows.Media.SolidColorBrush>, který je přiřazený <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border>.

 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]

 Tento ovládací prvek zodpovídá za definování států v rámci své kontrolní smlouvy, která je podrobněji popsána v tématu [přizpůsobení dalších ovládacích prvků pomocí porozumění kontraktu řízení](#customizing_other_controls_by_understanding_the_control_contract) dále v tomto tématu. V následující tabulce jsou uvedeny stavy, které jsou zadány pro <xref:System.Windows.Controls.Button>.

|Název VisualState|Název VisualStateGroup|Popis|
|----------------------|---------------------------|-----------------|
|Běžnou|CommonStates|Výchozí stav.|
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|
|Stisknete|CommonStates|Ovládací prvek se stiskne.|
|Zabezpečen|CommonStates|Ovládací prvek je zakázán.|
|Zaměřil|FocusStates|Ovládací prvek má fokus.|
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|

 <xref:System.Windows.Controls.Button> definuje dvě skupiny stavů: `CommonStates` skupina obsahuje `Normal`, `MouseOver`, `Pressed`a `Disabled` stavy. `FocusStates` skupina obsahuje stavy `Focused` a `Unfocused`. Stavy ve stejné skupině stavů se vzájemně vylučují. Ovládací prvek je vždy v přesně jednom stavu na skupinu. Například <xref:System.Windows.Controls.Button> může mít fokus i v případě, že ukazatel myši není nad ním, takže <xref:System.Windows.Controls.Button> ve stavu `Focused` může být ve stavu `MouseOver`, `Pressed`nebo `Normal`.

 Přidáte <xref:System.Windows.VisualState> objektů do objektů <xref:System.Windows.VisualStateGroup>. Přidáte <xref:System.Windows.VisualStateGroup> objekty do <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> připojené vlastnosti. Následující příklad definuje <xref:System.Windows.VisualState> objekty pro `Normal`, `MouseOver`a stavy `Pressed`, které jsou všechny ve skupině `CommonStates`. <xref:System.Windows.VisualState.Name%2A> každého <xref:System.Windows.VisualState> odpovídá názvu v předchozí tabulce. Stav `Disabled` a stavy ve skupině `FocusStates` jsou vynechány, aby byl příklad krátký, ale jsou obsaženy v celém příkladu na konci tohoto tématu.

> [!NOTE]
> Nezapomeňte nastavit <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> připojenou vlastnost v kořenovém <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>.

 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]

 Předchozí příklad vytvoří výstup podobný následujícímu obrázku.

 ![Tlačítko s šablonou vlastního ovládacího prvku.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Tlačítko, které používá vlastní šablonu ovládacího prvku v normálním stavu

 ![Tlačítko s červeným ohraničením.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Tlačítko, které používá vlastní šablonu ovládacího prvku ve stavu přetažení myší

 ![Ohraničení je transparentní pro tlačítko stisknuté.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")
Tlačítko, které používá vlastní šablonu ovládacího prvku ve stisknutém stavu

 Chcete-li najít vizuální stavy pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], přečtěte si téma [styly a šablony ovládacích prvků](control-styles-and-templates.md).

<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Určení chování ovládacího prvku při přechodu mezi stavy
 V předchozím příkladu se vzhled tlačítka také změní, když na něj uživatel klikne, ale pokud se tlačítko nestiskne po celou sekundu, uživatel se neprojeví. Ve výchozím nastavení trvá animace jedna sekunda. Vzhledem k tomu, že uživatelé budou muset tlačítko po celou dobu kliknout a uvolnit, nebude se vám projevit, pokud <xref:System.Windows.Controls.ControlTemplate> ve svém výchozím stavu.

 Můžete zadat dobu, po kterou bude trvat animace, aby došlo k plynulému převodu ovládacího prvku z jednoho stavu do druhého přidáním <xref:System.Windows.VisualTransition> objektů do <xref:System.Windows.Controls.ControlTemplate>. Při vytváření <xref:System.Windows.VisualTransition>zadáte jednu nebo více následujících možností:

- Čas potřebný k přechodu mezi stavy, které mají být provedeny.

- Další změny vzhledu ovládacího prvku, ke kterým dojde v době přechodu.

- Který uvádí, na které <xref:System.Windows.VisualTransition> se má použít.

### <a name="specifying-the-duration-of-a-transition"></a>Určení doby trvání přechodu
 Nastavením vlastnosti <xref:System.Windows.VisualTransition.GeneratedDuration%2A> můžete určit, jak dlouho trvá přechod. Předchozí příklad má <xref:System.Windows.VisualState>, který určuje, že ohraničení tlačítka bude při stisknutí tlačítka transparentní, ale pokud se tlačítko rychle stiskne a uvolní, animace trvá příliš dlouho. <xref:System.Windows.VisualTransition> můžete použít k určení doby, po kterou má ovládací prvek přejít do stisknutého stavu. Následující příklad určuje, že ovládací prvek převezme jedno setiny sekundy, aby přešl do stavu stisknuto.

 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]

### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Určení změn vzhledu ovládacího prvku během přechodu
 <xref:System.Windows.VisualTransition> obsahuje <xref:System.Windows.Media.Animation.Storyboard>, který začíná při přechodu ovládacího prvku mezi stavy. Můžete například určit, že k určité animaci dojde, když ovládací prvek přejde ze stavu `MouseOver` do stavu `Normal`. Následující příklad vytvoří <xref:System.Windows.VisualTransition>, který určuje, že když uživatel přesune ukazatel myši na tlačítko, změní se ohraničení tlačítka na modroo a potom na žlutou, a to na černou po 1,5 sekundách.

 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]

### <a name="specifying-when-a-visualtransition-is-applied"></a>Určení, kdy se používá VisualTransition
 <xref:System.Windows.VisualTransition> lze omezit na použití pouze v určitých stavech nebo je lze použít kdykoli, když ovládací prvek přechází mezi stavy. V předchozím příkladu je <xref:System.Windows.VisualTransition> použita, když ovládací prvek přejde ze stavu `MouseOver` do stavu `Normal`; v příkladu je použita <xref:System.Windows.VisualTransition>, když ovládací prvek přejde do stavu `Pressed`. Omezením použití <xref:System.Windows.VisualTransition> nastavením vlastností <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A>. V následující tabulce jsou popsány úrovně omezení od nejvíce omezující po nejméně omezující.

|Typ omezení|Hodnota z|Hodnota do|
|-------------------------|-------------------|-----------------|
|Z určeného stavu do jiného zadaného stavu|Název <xref:System.Windows.VisualState>|Název <xref:System.Windows.VisualState>|
|Ze všech stavů do zadaného stavu|Nenastaveno|Název <xref:System.Windows.VisualState>|
|Z určeného stavu do libovolného stavu|Název <xref:System.Windows.VisualState>|Nenastaveno|
|Z libovolného stavu do jakéhokoli jiného stavu|Nenastaveno|Nenastaveno|

 V <xref:System.Windows.VisualStateGroup> můžete mít více <xref:System.Windows.VisualTransition> objektů, které odkazují na stejný stav, ale budou použity v pořadí, v jakém je tato tabulka v předchozí tabulce. V následujícím příkladu jsou k dispozici dva objekty <xref:System.Windows.VisualTransition>. Když ovládací prvek přejde ze stavu `Pressed` do stavu `MouseOver`, bude použit <xref:System.Windows.VisualTransition>, který má <xref:System.Windows.VisualTransition.From%2A> a <xref:System.Windows.VisualTransition.To%2A> sada. Když ovládací prvek přejde ze stavu, který není `Pressed` do stavu `MouseOver`, je použit druhý stav.

 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]

 <xref:System.Windows.VisualStateGroup> má vlastnost <xref:System.Windows.VisualStateGroup.Transitions%2A>, která obsahuje objekty <xref:System.Windows.VisualTransition>, které se vztahují k <xref:System.Windows.VisualState> objektům v <xref:System.Windows.VisualStateGroup>. Jako autor <xref:System.Windows.Controls.ControlTemplate> nebudete mít k dispozici <xref:System.Windows.VisualTransition>, která chcete. Pokud jsou ale vlastnosti <xref:System.Windows.VisualTransition.To%2A> a <xref:System.Windows.VisualTransition.From%2A> nastavené na názvy stavů, které nejsou v <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> se ignoruje.

 Následující příklad ukazuje <xref:System.Windows.VisualStateGroup> pro `CommonStates`. V příkladu je definována <xref:System.Windows.VisualTransition> pro každé z následujících přechodů tlačítek.

- Do stavu `Pressed`.

- Do stavu `MouseOver`.

- Ze stavu `Pressed` do stavu `MouseOver`.

- Ze stavu `MouseOver` do stavu `Normal`.

 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]

<a name="customizing_other_controls_by_understanding_the_control_contract"></a>
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Přizpůsobení dalších ovládacích prvků pomocí porozumění kontraktu řízení
 Ovládací prvek, který používá <xref:System.Windows.Controls.ControlTemplate> k určení jeho vizuální struktury (pomocí objektů <xref:System.Windows.FrameworkElement>) a chování vizuálů (pomocí objektů <xref:System.Windows.VisualState>) používá model řízení částí. Tento model používá mnoho ovládacích prvků, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4. Části, o kterých <xref:System.Windows.Controls.ControlTemplate> autor musí vědět, se sdělují prostřednictvím kontraktu řízení. Pokud rozumíte částem kontraktu ovládacího prvku, můžete přizpůsobit vzhled libovolného ovládacího prvku, který používá model ovládacího prvku součásti.

 Kontrakt ovládacího prvku má tři prvky:

- Vizuální prvky, které logika ovládacího prvku používá.

- Stavy ovládacího prvku a skupiny, do kterých každý stav patří.

- Veřejné vlastnosti, které vizuálně ovlivňují ovládací prvek.

### <a name="visual-elements-in-the-control-contract"></a>Vizuální prvky v kontraktu řízení
 Logika ovládacího prvku někdy komunikuje s <xref:System.Windows.FrameworkElement>, který je v <xref:System.Windows.Controls.ControlTemplate>. Například ovládací prvek může zpracovat událost jednoho z jeho prvků. Když ovládací prvek očekává v <xref:System.Windows.Controls.ControlTemplate>najít konkrétní <xref:System.Windows.FrameworkElement>, musí předat tyto informace autorovi <xref:System.Windows.Controls.ControlTemplate>. Ovládací prvek používá <xref:System.Windows.TemplatePartAttribute> k vyjádření typu prvku, který je očekáván, a názvu elementu, který má být. <xref:System.Windows.Controls.Button> nemá v kontraktu řízení <xref:System.Windows.FrameworkElement> části, ale další ovládací prvky, jako je například <xref:System.Windows.Controls.ComboBox>, udělejte.

 Následující příklad ukazuje <xref:System.Windows.TemplatePartAttribute> objekty, které jsou zadány ve třídě <xref:System.Windows.Controls.ComboBox>. Logika <xref:System.Windows.Controls.ComboBox> očekává, že <xref:System.Windows.Controls.TextBox> s názvem `PART_EditableTextBox` a <xref:System.Windows.Controls.Primitives.Popup> s názvem `PART_Popup` v jeho <xref:System.Windows.Controls.ControlTemplate>.

 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]

 Následující příklad ukazuje zjednodušený <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ComboBox>, který obsahuje prvky, které jsou určeny objekty <xref:System.Windows.TemplatePartAttribute> třídy <xref:System.Windows.Controls.ComboBox>.

 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]

### <a name="states-in-the-control-contract"></a>Stavy v rámci kontraktu řízení
 Stavy ovládacího prvku jsou také součástí kontraktu ovládacího prvku. Příklad vytvoření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ukazuje, jak určit vzhled <xref:System.Windows.Controls.Button> v závislosti na jeho stavech. Vytvoříte <xref:System.Windows.VisualState> pro každý zadaný stav a vložíte všechny objekty <xref:System.Windows.VisualState> sdílející <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> v <xref:System.Windows.VisualStateGroup>, jak je popsáno v části [Změna vzhledu ovládacího prvku v závislosti na jeho stavu](#changing_the_appearance_of_a_control_depending_on_its_state) dříve v tomto tématu. Ovládací prvky třetích stran by měly určovat stavy pomocí <xref:System.Windows.TemplateVisualStateAttribute>, což umožňuje nástrojům návrháře, jako je [Návrhář XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio) v aplikaci Visual Studio a Blend pro Visual Studio, k vystavení stavů ovládacích prvků pro šablony pro vytváření obsahu.

 Chcete-li najít kontrakt řízení pro ovládací prvky, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], přečtěte si téma [styly a šablony ovládacích prvků](control-styles-and-templates.md).

### <a name="properties-in-the-control-contract"></a>Vlastnosti v kontraktu řízení
 Veřejné vlastnosti, které vizuálně ovlivňují ovládací prvek, jsou zahrnuty i v rámci kontraktu řízení. Tyto vlastnosti lze nastavit, chcete-li změnit vzhled ovládacího prvku bez vytvoření nové <xref:System.Windows.Controls.ControlTemplate>. Můžete také použít rozšíření značek [TemplateBinding](../advanced/templatebinding-markup-extension.md) k vázání vlastností prvků, které jsou v <xref:System.Windows.Controls.ControlTemplate> veřejných vlastností, které jsou definovány <xref:System.Windows.Controls.Button>.

 Následující příklad ukazuje kontrakt ovládacího prvku pro tlačítko.

 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]

 Při vytváření <xref:System.Windows.Controls.ControlTemplate>je často nejjednodušší začít s existujícím <xref:System.Windows.Controls.ControlTemplate> a provádět v něm změny. Chcete-li změnit existující <xref:System.Windows.Controls.ControlTemplate>, můžete provést jednu z následujících akcí:

- Použijte návrháře, jako je například Blend pro Visual Studio, který poskytuje grafické uživatelské rozhraní pro vytváření šablon ovládacích prvků. Další informace naleznete v tématu [stylování ovládacího prvku, který podporuje šablony](https://go.microsoft.com/fwlink/?LinkId=161153).

- Získá výchozí <xref:System.Windows.Controls.ControlTemplate> a upraví ho. Chcete-li najít výchozí šablony ovládacích prvků, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], přečtěte si téma [výchozí motivy WPF](https://go.microsoft.com/fwlink/?LinkID=158252).

<a name="complete_example"></a>
## <a name="complete-example"></a>Kompletní příklad
 Následující příklad ukazuje kompletní <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>, která jsou popsána v tomto tématu.

 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]

## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
