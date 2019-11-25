---
title: Vytvoření ovládacího prvku se vzhledem, který lze přizpůsobit
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: d9cf092cf47d4fb70b15033d039777d3279b633a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283562"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Vytvoření ovládacího prvku se vzhledem, který lze přizpůsobit

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vám dává možnost vytvořit ovládací prvek, jehož vzhled se dá přizpůsobit. Můžete například změnit vzhled <xref:System.Windows.Controls.CheckBox> nad rámec toho, co nastavení vlastností provede vytvořením nového <xref:System.Windows.Controls.ControlTemplate>. Následující ilustrace znázorňuje <xref:System.Windows.Controls.CheckBox>, která používá výchozí <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.CheckBox>, která používá vlastní <xref:System.Windows.Controls.ControlTemplate>.

![Zaškrtávací políčko s výchozí šablonou ovládacího prvku.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Zaškrtávací políčko, které používá výchozí šablonu ovládacího prvku

![Zaškrtávací políčko s šablonou vlastního ovládacího prvku.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Zaškrtávací políčko, které používá vlastní šablonu ovládacího prvku

Pokud při vytváření ovládacího prvku budete postupovat podle modelu částí a stavů, bude možné vzhled ovládacího prvku přizpůsobit. Nástroje návrháře, jako je například Blend pro Visual Studio podporují model komponent a stavů, takže když použijete tento model, váš ovládací prvek bude přizpůsobitelný v těchto typech aplikací.  Toto téma popisuje model částí a stavů a postup, jak ho sledovat při vytváření vlastního ovládacího prvku. Toto téma používá příklad vlastního ovládacího prvku `NumericUpDown`k ilustraci filozofie tohoto modelu.  Ovládací prvek `NumericUpDown` zobrazí číselnou hodnotu, kterou může uživatel zvětšit nebo zmenšit kliknutím na tlačítka ovládacího prvku.  Následující ilustrace znázorňuje ovládací prvek `NumericUpDown`, který je popsán v tomto tématu.

![Vlastní ovládací prvek NumericUpDown](./media/ndp-numericupdown.png "NDP_NumericUPDown")
Vlastní ovládací prvek NumericUpDown

Toto téma obsahuje následující oddíly:

- [Požadavky](#prerequisites)

- [Model částí a stavů](#parts_and_states_model)

- [Definování vizuální struktury a vizuálního chování ovládacího prvku v ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [Použití částí ControlTemplate v kódu](#using_parts_of_the_controltemplate_in_code)

- [Poskytování kontraktu řízení](#providing_the_control_contract)

- [Kompletní příklad](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

V tomto tématu se předpokládá, že víte, jak vytvořit novou <xref:System.Windows.Controls.ControlTemplate> pro existující ovládací prvek, jsou obeznámené s tím, co jsou prvky na kontraktu ovládacího prvku, a pochopení konceptů popsaných v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).

> [!NOTE]
> Chcete-li vytvořit ovládací prvek, který může mít vlastní vzhled, je nutné vytvořit ovládací prvek, který dědí z třídy <xref:System.Windows.Controls.Control> nebo jedné z jeho podtříd jiných než <xref:System.Windows.Controls.UserControl>.  Ovládací prvek, který dědí z <xref:System.Windows.Controls.UserControl> je ovládací prvek, který lze rychle vytvořit, ale nepoužívá <xref:System.Windows.Controls.ControlTemplate> a nelze přizpůsobit jeho vzhled.

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>Model částí a stavů

Model součásti a stavy určuje, jak definovat vizuální strukturu a vizuální chování ovládacího prvku. Chcete-li postupovat podle modelu součásti a stavy, postupujte následovně:

- Definujte vizuální strukturu a vizuální chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku.

- Použijte určité osvědčené postupy, když logika ovládacího prvku komunikuje s částmi šablony ovládacího prvku.

- Poskytněte kontrakt ovládacího prvku, který určuje, co by mělo být zahrnuto do <xref:System.Windows.Controls.ControlTemplate>.

Při definování vizuální struktury a vizuálního chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku mohou autoři aplikace změnit vizuální strukturu a vizuální chování ovládacího prvku vytvořením nového <xref:System.Windows.Controls.ControlTemplate> namísto psaní kódu.   Je nutné zadat kontrakt řízení, který sděluje autorům aplikace, které <xref:System.Windows.FrameworkElement> objekty a stavy by měly být definovány v <xref:System.Windows.Controls.ControlTemplate>. Při interakci s částmi v <xref:System.Windows.Controls.ControlTemplate> byste měli dodržovat některé osvědčené postupy, aby ovládací prvek správně nedokončil nekompletní <xref:System.Windows.Controls.ControlTemplate>.  Pokud budete postupovat podle těchto tří principů, autoři aplikací budou moci vytvářet <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek stejně snadno, jako mohou pro ovládací prvky dodávané s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  V následující části jsou podrobněji vysvětlena všechna tato doporučení.

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definování vizuální struktury a vizuálního chování ovládacího prvku v ControlTemplate

Při vytváření vlastního ovládacího prvku pomocí modelu části a stavy můžete definovat vizuální strukturu ovládacího prvku a vizuální chování v jeho <xref:System.Windows.Controls.ControlTemplate> místo v jeho logice.  Vizuální struktura ovládacího prvku je složený z <xref:System.Windows.FrameworkElement> objektů, které tvoří ovládací prvek.  Chování vizuálu je způsob, jakým se ovládací prvek zobrazuje, když je v určitém stavu.   Další informace o vytváření <xref:System.Windows.Controls.ControlTemplate>, které určují vizuální strukturu a vizuální chování ovládacího prvku, naleznete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).

V příkladu ovládacího prvku `NumericUpDown` obsahuje vizuální struktura dva ovládací prvky <xref:System.Windows.Controls.Primitives.RepeatButton> a <xref:System.Windows.Controls.TextBlock>.  Pokud přidáte tyto ovládací prvky do kódu `NumericUpDown` ovládacího prvku – v jeho konstruktoru, například, umístění těchto ovládacích prvků by nebylo možné změnit.  Namísto definování vizuální struktury ovládacího prvku a vizuálního chování ve svém kódu byste jej měli definovat v <xref:System.Windows.Controls.ControlTemplate>.  Pak vývojář aplikace Přizpůsobte pozici tlačítek a <xref:System.Windows.Controls.TextBlock> a určete, k jakým chování dochází, když je `Value` záporné, protože <xref:System.Windows.Controls.ControlTemplate> může být nahrazena.

Následující příklad ukazuje vizuální strukturu ovládacího prvku `NumericUpDown`, který obsahuje <xref:System.Windows.Controls.Primitives.RepeatButton> ke zvýšení `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> pro snížení `Value`a <xref:System.Windows.Controls.TextBlock> k zobrazení `Value`.

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

Vizuální chování ovládacího prvku `NumericUpDown` je, že hodnota je červeným písmem, pokud je záporná.  Pokud změníte <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> v kódu, když je `Value` záporné, `NumericUpDown` se vždycky zobrazí červená záporná hodnota. Chování ovládacího prvku v <xref:System.Windows.Controls.ControlTemplate> zadáte přidáním <xref:System.Windows.VisualState> objektů do <xref:System.Windows.Controls.ControlTemplate>.  Následující příklad ukazuje <xref:System.Windows.VisualState> objekty pro `Positive` a `Negative` stavy.  `Positive` a `Negative` se vzájemně vylučují (ovládací prvek je vždycky v jednom z těchto dvou), takže v příkladu se objekty <xref:System.Windows.VisualState> vloží do jednoho <xref:System.Windows.VisualStateGroup>.  Když se ovládací prvek přejde do stavu `Negative`, <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> se změní na červenou.  Když je ovládací prvek ve stavu `Positive`, <xref:System.Windows.Controls.TextBlock.Foreground%2A> se vrátí na původní hodnotu.  Definování objektů <xref:System.Windows.VisualState> v <xref:System.Windows.Controls.ControlTemplate> je dále popsáno v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).

> [!NOTE]
> Nezapomeňte nastavit <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> připojenou vlastnost v kořenovém <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>Použití částí ControlTemplate v kódu

<xref:System.Windows.Controls.ControlTemplate> autor může vynechat objekty <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState>, buď záměrně nebo omylem, ale logika ovládacího prvku může tyto součásti potřebovat správně fungovat. Model součásti a stavy určuje, že váš ovládací prvek by měl být odolný vůči <xref:System.Windows.Controls.ControlTemplate>, který postrádá objekty <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState>.  Váš ovládací prvek by neměl vyvolat výjimku nebo ohlásit chybu, pokud v <xref:System.Windows.Controls.ControlTemplate>chybí <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>nebo <xref:System.Windows.VisualStateGroup>. Tato část popisuje doporučené postupy pro interakci s <xref:System.Windows.FrameworkElement>mi objekty a správou stavů.

### <a name="anticipate-missing-frameworkelement-objects"></a>Předvídání chybějících objektů FrameworkElement

Při definování <xref:System.Windows.FrameworkElement> objektů v <xref:System.Windows.Controls.ControlTemplate>může logika ovládacího prvku vyžadovat interakci s některými z nich.  Například `NumericUpDown` ovládací prvek se přihlásí k odběru tlačítek ' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události pro zvýšení nebo snížení `Value` a nastaví vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> na `Value`. Pokud vlastní <xref:System.Windows.Controls.ControlTemplate> vynechá <xref:System.Windows.Controls.TextBlock> nebo tlačítka, je přijatelné, že ovládací prvek ztratí některé z jeho funkcí, ale měli byste se ujistit, že váš ovládací prvek nezpůsobí chybu. Pokud například <xref:System.Windows.Controls.ControlTemplate> neobsahuje tlačítka pro změnu `Value`, `NumericUpDown` ztratí tuto funkci, ale aplikace, která <xref:System.Windows.Controls.ControlTemplate> používá, bude nadále běžet.

Následující postupy zajistí, že ovládací prvek bude správně reagovat na chybějící <xref:System.Windows.FrameworkElement> objekty:

1. Nastavte atribut `x:Name` pro každý <xref:System.Windows.FrameworkElement>, na který musíte odkazovat v kódu.

2. Definujte soukromé vlastnosti pro každý <xref:System.Windows.FrameworkElement>, se kterými potřebujete pracovat.

3. Přihlaste se k odběru a odhlaste se k odběru všech událostí, které ovládací prvek zpracovává v přístupovém objektu set vlastnosti <xref:System.Windows.FrameworkElement>.

4. Nastavte vlastnosti <xref:System.Windows.FrameworkElement>, které jste definovali v kroku 2 v metodě <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>. Toto je nejstarší, že <xref:System.Windows.FrameworkElement> v <xref:System.Windows.Controls.ControlTemplate> jsou k dispozici pro ovládací prvek. Pomocí `x:Name` <xref:System.Windows.FrameworkElement> je můžete získat z <xref:System.Windows.Controls.ControlTemplate>.

5. Před přístupem ke svým členům ověřte, zda <xref:System.Windows.FrameworkElement> není `null`.  Pokud je `null`, neohlaste chybu.

Následující příklady ukazují, jak `NumericUpDown` ovládací prvek komunikuje s objekty <xref:System.Windows.FrameworkElement> v souladu s doporučeními v předchozím seznamu.

V příkladu, který definuje vizuální strukturu `NumericUpDown` ovládacího prvku v <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton>, která zvyšuje `Value` má atribut `x:Name` nastaven na `UpButton`.  Následující příklad deklaruje vlastnost nazvanou `UpButtonElement`, která představuje <xref:System.Windows.Controls.Primitives.RepeatButton> deklarované v <xref:System.Windows.Controls.ControlTemplate>. Přístupový objekt `set` nejdřív zruší odběr události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka, pokud `UpDownElement` `null`, nastaví vlastnost a pak se přihlásí k odběru události <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. K dispozici je také vlastnost, která zde není zobrazena, pro druhý <xref:System.Windows.Controls.Primitives.RepeatButton>volána `DownButtonElement`.

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

Následující příklad ukazuje <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pro ovládací prvek `NumericUpDown`.  V příkladu se používá metoda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> k získání objektů <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  Všimněte si, že příklad chrání proti případům, kde <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> najde <xref:System.Windows.FrameworkElement> se zadaným názvem, který není očekávaného typu. Je také osvědčeným postupem ignorovat prvky, které mají zadanou `x:Name`, ale jsou nesprávného typu.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Podle postupů uvedených v předchozích příkladech se ujistěte, že se ovládací prvek bude nadále spouštět, i když <xref:System.Windows.Controls.ControlTemplate> chybí <xref:System.Windows.FrameworkElement>.

### <a name="use-the-visualstatemanager-to-manage-states"></a>Použití VisualStateManager ke správě stavů

<xref:System.Windows.VisualStateManager> udržuje přehled o stavech ovládacího prvku a provádí logiku potřebnou k přechodu mezi stavy. Když do <xref:System.Windows.Controls.ControlTemplate>přidáte <xref:System.Windows.VisualState> objekty, přidáte je do <xref:System.Windows.VisualStateGroup> a přidáte <xref:System.Windows.VisualStateGroup> do vlastnosti <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> připojené, aby k nim <xref:System.Windows.VisualStateManager> přístup.

Následující příklad opakuje předchozí příklad, který ukazuje <xref:System.Windows.VisualState> objekty, které odpovídají `Positive` a `Negative` stavů ovládacího prvku. <xref:System.Windows.Media.Animation.Storyboard> v `Negative`<xref:System.Windows.VisualState> zapne <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> červeně.   Když je ovládací prvek `NumericUpDown` ve stavu `Negative`, začíná scénář ve stavu `Negative`.  Pak <xref:System.Windows.Media.Animation.Storyboard> ve stavu `Negative` zastaví, když se ovládací prvek vrátí do `Positive` stavu.  `Positive`<xref:System.Windows.VisualState> nemusí obsahovat <xref:System.Windows.Media.Animation.Storyboard>, protože když se <xref:System.Windows.Media.Animation.Storyboard> pro `Negative` zastaví, <xref:System.Windows.Controls.TextBlock.Foreground%2A> se vrátí do původní barvy.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

Všimněte si, že <xref:System.Windows.Controls.TextBlock> má daný název, ale <xref:System.Windows.Controls.TextBlock> není v kontraktu ovládacího prvku pro `NumericUpDown`, protože logika ovládacího prvku nikdy neodkazuje na <xref:System.Windows.Controls.TextBlock>.  Prvky, které jsou odkazovány v <xref:System.Windows.Controls.ControlTemplate> mají názvy, ale nemusejí být součástí kontraktu řízení, protože nový <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku nemusí být odkazován na tento prvek.  Například někdo, který vytvoří novou <xref:System.Windows.Controls.ControlTemplate> pro `NumericUpDown`, se může rozhodnout, že `Value` je negativní, změnou <xref:System.Windows.Controls.Control.Foreground%2A>.  V takovém případě ani kód ani <xref:System.Windows.Controls.ControlTemplate> neodkazují na <xref:System.Windows.Controls.TextBlock> podle názvu.

Logika ovládacího prvku zodpovídá za změnu stavu ovládacího prvku. Následující příklad ukazuje, že ovládací prvek `NumericUpDown` volá metodu <xref:System.Windows.VisualStateManager.GoToState%2A> a přejde do stavu `Positive`, pokud `Value` je 0 nebo vyšší a `Negative` stav, pokud je `Value` menší než 0.

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

Metoda <xref:System.Windows.VisualStateManager.GoToState%2A> provádí logiku potřebnou ke správnému spuštění a zastavení scénářů. Když ovládací prvek volá <xref:System.Windows.VisualStateManager.GoToState%2A> ke změně jeho stavu, <xref:System.Windows.VisualStateManager> provede následující:

- Pokud <xref:System.Windows.VisualState>, na které ovládací prvek bude mít <xref:System.Windows.Media.Animation.Storyboard>, začne scénář. V případě, že <xref:System.Windows.VisualState>, ze kterého ovládací prvek přichází, má <xref:System.Windows.Media.Animation.Storyboard>, scénář skončí.

- Pokud je ovládací prvek již ve stavu, který je zadán, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `true`.

- Pokud stav, který je zadán, neexistuje v <xref:System.Windows.Controls.ControlTemplate> `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `false`.

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Osvědčené postupy pro práci s VisualStateManager

Chcete-li zachovat stavy vašeho ovládacího prvku, doporučujeme provést následující akce:

- Ke sledování jeho stavu použijte vlastnosti.

- Vytvořte pomocnou metodu pro přechod mezi stavy.

Ovládací prvek `NumericUpDown` používá jeho vlastnost `Value` ke sledování, zda je ve stavu `Positive` nebo `Negative`.  Ovládací prvek `NumericUpDown` také definuje `Focused` a `UnFocused` stavy, které sledují vlastnost <xref:System.Windows.UIElement.IsFocused%2A>. Pokud používáte stavy, které přirozeně neodpovídají vlastnosti ovládacího prvku, můžete definovat vlastnost Private pro sledování stavu.

Jediná metoda, která aktualizuje všechny stavy, centralizace volá do <xref:System.Windows.VisualStateManager> a udržuje kód spravovaný. Následující příklad ukazuje pomocnou metodu ovládacího prvku `NumericUpDown`, `UpdateStates`. Když `Value` je větší nebo rovno 0, <xref:System.Windows.Controls.Control> je ve stavu `Positive`.  Pokud je `Value` menší než 0, ovládací prvek je ve stavu `Negative`.  Pokud je <xref:System.Windows.UIElement.IsFocused%2A> `true`, je ovládací prvek ve stavu `Focused`; v opačném případě je ve stavu `Unfocused`.  Ovládací prvek může volat `UpdateStates`, kdykoli potřebuje změnit svůj stav bez ohledu na to, jaké změny stavu.

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

Pokud předáte název stavu <xref:System.Windows.VisualStateManager.GoToState%2A>, když je ovládací prvek již v tomto stavu, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci, takže nemusíte kontrolovat aktuální stav ovládacího prvku.  Například pokud `Value` změny z jednoho záporného čísla na jiné záporné číslo, scénář pro `Negative` stav není přerušen a uživatel se v ovládacím prvku nezobrazuje žádná změna.

<xref:System.Windows.VisualStateManager> používá objekty <xref:System.Windows.VisualStateGroup> k určení stavu, který se má ukončit při volání <xref:System.Windows.VisualStateManager.GoToState%2A>. Ovládací prvek je vždy v jednom stavu pro každý <xref:System.Windows.VisualStateGroup> definovaný v jeho <xref:System.Windows.Controls.ControlTemplate> a opustí stav, když přejde do jiného stavu ze stejného <xref:System.Windows.VisualStateGroup>. Například <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku `NumericUpDown` definuje `Positive` a `Negative`objekty <xref:System.Windows.VisualState> v jednom <xref:System.Windows.VisualStateGroup> a `Focused` a `Unfocused`objekty <xref:System.Windows.VisualState> v jiném. (V části [kompletní příklad](#complete_example) v tomto tématu se můžete podívat na `Focused` a `Unfocused`<xref:System.Windows.VisualState>, když ovládací prvek přejde ze stavu `Positive` do stavu `Negative`, nebo naopak, ovládací prvek zůstane ve stavu `Focused` nebo `Unfocused`.

Existují tři obvyklá místa, kde se může změnit stav ovládacího prvku:

- Když se <xref:System.Windows.Controls.ControlTemplate> aplikuje na <xref:System.Windows.Controls.Control>.

- Při změně vlastnosti.

- Při výskytu události.

Následující příklady ukazují, jak aktualizovat stav ovládacího prvku `NumericUpDown` v těchto případech.

Měli byste aktualizovat stav ovládacího prvku v metodě <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> tak, aby se ovládací prvek zobrazil ve správném stavu při použití <xref:System.Windows.Controls.ControlTemplate>. Následující příklad volá `UpdateStates` v <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>, aby se zajistilo, že se ovládací prvek nachází v příslušných stavech.  Předpokládejme například, že vytvoříte ovládací prvek `NumericUpDown` a potom nastavíte jeho <xref:System.Windows.Controls.Control.Foreground%2A> na zelenou a `Value` na-5.  Pokud nevoláte `UpdateStates` při použití <xref:System.Windows.Controls.ControlTemplate> na ovládací prvek `NumericUpDown`, ovládací prvek není ve stavu `Negative` a hodnota je zelená namísto Red.  Je nutné volat `UpdateStates` pro vložení ovládacího prvku do stavu `Negative`.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Při změně vlastnosti často potřebujete aktualizovat stavy ovládacího prvku. Následující příklad ukazuje celou metodu `ValueChangedCallback`. Vzhledem k tomu, že je volána `ValueChangedCallback` při `Value` změně, metoda volá `UpdateStates` v případě, `Value` se změnily z pozitivního na záporné nebo naopak. Je přijatelné volat `UpdateStates`, když `Value` změní, ale zůstává kladné nebo záporné, protože v takovém případě ovládací prvek nezmění stavy.

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

Pokud dojde k události, může být také nutné aktualizovat stavy. Následující příklad ukazuje, že `NumericUpDown` volá `UpdateStates` na <xref:System.Windows.Controls.Control> pro zpracování události <xref:System.Windows.UIElement.GotFocus>.

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

<xref:System.Windows.VisualStateManager> vám pomůže se správou stavů vašeho ovládacího prvku. Pomocí <xref:System.Windows.VisualStateManager>zajistíte, aby ovládací prvek správně přechází mezi stavy.  Pokud budete postupovat podle doporučení popsaných v této části pro práci s <xref:System.Windows.VisualStateManager>, kód ovládacího prvku zůstane čitelný a udržovatelný.

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>Poskytování kontraktu řízení

Poskytnete kontrakt řízení, aby <xref:System.Windows.Controls.ControlTemplate> autoři věděli, co umístit do šablony. Kontrakt ovládacího prvku má tři prvky:

- Vizuální prvky, které logika ovládacího prvku používá.

- Stavy ovládacího prvku a skupiny, do kterých každý stav patří.

- Veřejné vlastnosti, které vizuálně ovlivňují ovládací prvek.

Někdo, který vytvoří nový <xref:System.Windows.Controls.ControlTemplate> potřebuje znát, co <xref:System.Windows.FrameworkElement> objekty logiky ovládacího prvku, jaký typ každého objektu je a jaký je jeho název. <xref:System.Windows.Controls.ControlTemplate> autor také musí znát název každého možného stavu, ve kterém se ovládací prvek může nacházet a který <xref:System.Windows.VisualStateGroup> stavu.

Návrat do `NumericUpDown`ového příkladu, ovládací prvek očekává, že <xref:System.Windows.Controls.ControlTemplate> mají následující objekty <xref:System.Windows.FrameworkElement>:

- <xref:System.Windows.Controls.Primitives.RepeatButton> s názvem `UpButton`.

- <xref:System.Windows.Controls.Primitives.RepeatButton> s názvem `DownButton.`

 Ovládací prvek může být v následujících stavech:

- V `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- V `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

Chcete-li určit, co <xref:System.Windows.FrameworkElement> objekty, které ovládací prvek očekává, použijte <xref:System.Windows.TemplatePartAttribute>, který určuje název a typ očekávaných prvků.  Chcete-li určit možné stavy ovládacího prvku, použijte <xref:System.Windows.TemplateVisualStateAttribute>, který určuje název stavu a který <xref:System.Windows.VisualStateGroup> patří do.  Do definice třídy ovládacího prvku vložte <xref:System.Windows.TemplatePartAttribute> a <xref:System.Windows.TemplateVisualStateAttribute>.

Jakákoli veřejná vlastnost, která má vliv na vzhled vašeho ovládacího prvku, je také součástí kontraktu řízení.

Následující příklad určuje <xref:System.Windows.FrameworkElement> objekt a stavy pro ovládací prvek `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>Kompletní příklad

Následující příklad je celý <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek `NumericUpDown`.

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

Následující příklad ukazuje logiku pro `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>Viz také:

- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
