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
ms.openlocfilehash: 171f9c4264825d1bdf0ba06e1e24b17eb8e8194f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623713"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Vytvoření ovládacího prvku se vzhledem, který lze přizpůsobit
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje možnost vytvářet ovládací prvek, jehož vzhledu lze přizpůsobit. Například můžete změnit vzhled <xref:System.Windows.Controls.CheckBox> rámec toho, jaká nastavení vlastnosti provede vytvořením nového <xref:System.Windows.Controls.ControlTemplate>. Následující ilustrace ukazuje <xref:System.Windows.Controls.CheckBox> , který používá výchozí <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.CheckBox> , která používá vlastní <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Zaškrtávací políčko pomocí výchozí šablony ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaškrtávací políčko, který používá výchozí šablonu ovládacího prvku  
  
 ![Zaškrtávací políčko se šablonou vlastního ovládacího prvku. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaškrtávací políčko, který používá šablonu vlastního ovládacího prvku  
  
 Pokud budete postupovat podle modelu částí a stavy při vytvoření ovládacího prvku, bude lze přizpůsobit vzhled ovládacího prvku. Návrhářské nástroje, jako je například Microsoft Expression Blend podporu částí a stavů modelu, takže pokud budete postupovat podle tohoto modelu bude váš ovládací prvek přizpůsobitelné tyto typy aplikací.  Toto téma popisuje model částí a stavy a jak na něho při vytváření vlastního ovládacího prvku. Toto téma používá příklad vlastního ovládacího prvku `NumericUpDown`, k objasnění filozofií tohoto modelu.  `NumericUpDown` Ovládací prvek zobrazí číselná hodnota, která uživatel může zvýšit nebo snížit po kliknutí na ovládací prvek tlačítka.  Je vidět na následujícím obrázku `NumericUpDown` ovládací prvek, který je popsán v tomto tématu.  
  
 ![Vlastní ovládací prvek NumericUpDown. ](../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
Vlastní ovládací prvek NumericUpDown  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Požadavky](#prerequisites)  
  
-   [Části a stavů modelu](#parts_and_states_model)  
  
-   [Definování vizuální struktury a vizuální chování ovládacího prvku v objektu ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Pomocí části ControlTemplate v kódu](#using_parts_of_the_controltemplate_in_code)  
  
-   [Poskytuje kontrakt ovládacího prvku](#providing_the_control_contract)  
  
-   [Kompletní příklad](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že víte, jak vytvořit nový <xref:System.Windows.Controls.ControlTemplate> pro existující ovládací prvek, obeznámeni s co jsou prvky na kontrakt ovládacího prvku a seznamte se s principy probírané v [přizpůsobení vzhledu stávajícího ovládacího prvku pomocí Vytvoření objektu ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Vytvoření ovládacího prvku, který může mít jeho vzhled, upravit, musíte vytvořit ovládací prvek, který dědí z <xref:System.Windows.Controls.Control> třída nebo jedna z jejích podtříd jiných než <xref:System.Windows.Controls.UserControl>.  Ovládací prvek, který dědí z <xref:System.Windows.Controls.UserControl> je ovládací prvek, který je možné rychle vytvořit, ale nepoužívá <xref:System.Windows.Controls.ControlTemplate> a nelze přizpůsobit její vzhled.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Části a stavů modelu  
 Částí a stavy model Určuje, jak se používá k definování vizuální struktury a chování ovládacího prvku visual. Postupovat podle částí a stavů modelu, proveďte následující:  
  
-   Definování vizuální struktury a vizuální chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku.  
  
-   Postupujte podle některých osvědčených postupů při logiky ovládacího prvku interakci s části šablony ovládacích prvků.  
  
-   Zadejte kontrakt ovládacího prvku k určení, co by měl být součástí <xref:System.Windows.Controls.ControlTemplate>.  
  
 Při definování vizuální struktury a vizuální chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku, autoři aplikace můžete změnit vizuální struktury a vizuální chování ovládacího prvku vytvořením nového <xref:System.Windows.Controls.ControlTemplate> místo psaní kódu.   Je nutné zadat autory kontrakt ovládacího prvku, který Instruuje aplikaci, která <xref:System.Windows.FrameworkElement> objekty a stavy musí být definován v <xref:System.Windows.Controls.ControlTemplate>. Měli byste postupovat podle některých osvědčených postupů při interakci s částmi v <xref:System.Windows.Controls.ControlTemplate> tak, aby váš ovládací prvek správně zpracovává neúplnou <xref:System.Windows.Controls.ControlTemplate>.  Pokud budete postupovat podle těchto tří zásad, autoři aplikace budou moci vytvářet <xref:System.Windows.Controls.ControlTemplate> jenom ovládacího prvku stejně snadno, jako jsou ovládací prvky, které zaslat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Následující část podává přehled o každé z těchto doporučení podrobně.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definování vizuální struktury a vizuální chování ovládacího prvku v objektu ControlTemplate  
 Při vytváření vlastního ovládacího prvku s použitím modelu částí a stavy definování vizuální struktury a vizuální chování v ovládacího prvku jeho <xref:System.Windows.Controls.ControlTemplate> místo svou logikou.  Vizuální struktury ovládací prvek je složený z <xref:System.Windows.FrameworkElement> objekty, které tvoří ovládacího prvku.  Vizuální chování je způsob, jakým ovládací prvek se zobrazí, když je v určitých stavu.   Další informace o vytváření <xref:System.Windows.Controls.ControlTemplate> , který určuje vizuální struktury a vizuální chování ovládacího prvku, naleznete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 V příkladu `NumericUpDown` ovládacího prvku, vizuální struktury zahrnuje dva <xref:System.Windows.Controls.Primitives.RepeatButton> ovládací prvky a <xref:System.Windows.Controls.TextBlock>.  Pokud chcete přidat tyto ovládací prvky v kódu `NumericUpDown` ovládacího prvku – v konstruktoru, například pozice tyto ovládací prvky by být změnit.  Místo definování vizuální struktury a vizuální chování ovládacího prvku v jeho kód, byste měli definovat v <xref:System.Windows.Controls.ControlTemplate>.  Potom vývojář aplikace k přizpůsobení umístění tlačítek a <xref:System.Windows.Controls.TextBlock> a určete, jaké chování při `Value` je záporný protože <xref:System.Windows.Controls.ControlTemplate> lze nahradit.  
  
 Následující příklad ukazuje strukturu visual `NumericUpDown` ovládací prvek, který zahrnuje <xref:System.Windows.Controls.Primitives.RepeatButton> zvýšit `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> snížení `Value`a <xref:System.Windows.Controls.TextBlock> zobrazíte `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Vizuální chování `NumericUpDown` ovládací prvek je, že hodnota je v red písma, pokud je záporné.  Pokud změníte <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> v kódu při `Value` je záporný, `NumericUpDown` vždy zobrazí červený zápornou hodnotu. Zadejte visual chování ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> přidáním <xref:System.Windows.VisualState> objektů <xref:System.Windows.Controls.ControlTemplate>.  Následující příklad ukazuje <xref:System.Windows.VisualState> pro objekty `Positive` a `Negative` stavy.  `Positive` a `Negative` jsou vzájemně se vylučující (ovládací prvek, je vždy přesně jeden z nich), takže se v příkladu se umístí <xref:System.Windows.VisualState> objekty do jednoho <xref:System.Windows.VisualStateGroup>.  Při přechodu ovládací prvek do `Negative` stavu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> zčervená.  Pokud je ovládací prvek v `Positive` stavu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> vrátí na něj původní hodnotu.  Definování <xref:System.Windows.VisualState> objekty v <xref:System.Windows.Controls.ControlTemplate> je popsána dále v [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Nezapomeňte nastavit <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost v kořenovém adresáři <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Pomocí části ControlTemplate v kódu  
 A <xref:System.Windows.Controls.ControlTemplate> Autor může vynechat <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState> objekty záměrně nebo omylem, ale logiky ovládacího prvku může být nutné tyto součásti fungovat správně. Částí a stavy model Určuje, že ovládací prvek by měl být odolné vůči <xref:System.Windows.Controls.ControlTemplate> , kde chybí <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState> objekty.  Ovládacího prvku by neměl vyvolá výjimku nebo sestavy chybu, pokud <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, nebo <xref:System.Windows.VisualStateGroup> chybí <xref:System.Windows.Controls.ControlTemplate>. Tato část popisuje doporučené postupy pro interakci s <xref:System.Windows.FrameworkElement> objektů a správa stavů.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Příprava na vyčerpání chybí FrameworkElement – objekty  
 Při definování <xref:System.Windows.FrameworkElement> objekty v <xref:System.Windows.Controls.ControlTemplate>, logiky ovládacího prvku může být nutné k interakci s některé z nich.  Například `NumericUpDown` ovládací prvek přihlásí na tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události chcete zvýšit nebo snížit `Value` a nastaví <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost <xref:System.Windows.Controls.TextBlock> k `Value`. Pokud vlastní <xref:System.Windows.Controls.ControlTemplate> vynechává <xref:System.Windows.Controls.TextBlock> nebo tlačítka, je to přijatelné, že ovládací prvek ztratí některé ze svých funkcí, ale měli byste být jisti, že ovládací prvek nezpůsobí chybu. Například pokud <xref:System.Windows.Controls.ControlTemplate> neobsahuje tlačítka, chcete-li změnit `Value`, `NumericUpDown` ztratí, které tuto funkci, ale aplikace, která se používá <xref:System.Windows.Controls.ControlTemplate> budou nadále spuštěné.  
  
 Následující postupy se zajistí, že ovládací prvek správně reaguje na chybějící <xref:System.Windows.FrameworkElement> objekty:  
  
1.  Nastavte `x:Name` atribut pro každý <xref:System.Windows.FrameworkElement> , budete muset odkaz v kódu.  
  
2.  Definovat privátní vlastnosti pro každý <xref:System.Windows.FrameworkElement> vyžadující interakci s.  
  
3.  Přihlášení a odhlášení ze všech událostí, které váš ovládací prvek zpracovává v <xref:System.Windows.FrameworkElement> vlastnost nastaví přístupový objekt.  
  
4.  Nastavte <xref:System.Windows.FrameworkElement> vlastnosti, které jste definovali v kroku 2 v <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metody. Toto je první, který <xref:System.Windows.FrameworkElement> v <xref:System.Windows.Controls.ControlTemplate> je k dispozici pro ovládací prvek. Použití `x:Name` z <xref:System.Windows.FrameworkElement> zobrazíte ho <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Zkontrolujte, že <xref:System.Windows.FrameworkElement> není `null` před přístupem k jeho členů.  Pokud je `null`, není hlášena chyba.  
  
 Následující příklady ukazují jak `NumericUpDown` ovládací prvek komunikuje s <xref:System.Windows.FrameworkElement> objekty v souladu s doporučení v předchozím seznamu.  
  
 V následujícím příkladu definuje strukturu visual `NumericUpDown` v ovládacím prvku <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> , který zvyšuje `Value` má jeho `x:Name` atribut nastaven na `UpButton`.  Následující příklad deklaruje vlastnost s názvem `UpButtonElement` , která představuje <xref:System.Windows.Controls.Primitives.RepeatButton> , která je deklarována v <xref:System.Windows.Controls.ControlTemplate>. `set` Přistupující objekt nejprve zrušení odběru na tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události Pokud `UpDownElement` není `null`, nastaví vlastnost a potom se přihlásí k odběru <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. Je také vlastnost definovaná, ale zde nejsou uvedené, pro ostatní <xref:System.Windows.Controls.Primitives.RepeatButton>, označované jako `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 Následující příklad ukazuje <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pro `NumericUpDown` ovládacího prvku.  V příkladu se používá <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodu k získání <xref:System.Windows.FrameworkElement> objekty z <xref:System.Windows.Controls.ControlTemplate>.  Všimněte si, že v příkladu budete chráněni před případech, kdy <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> najde <xref:System.Windows.FrameworkElement> se zadaným názvem, který není očekávaného typu. Je také vhodné ignorovat prvky, které mají zadanou `x:Name` , ale jsou chybného typu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Pomocí následujících postupů, které jsou uvedeny v předchozích příkladech, zajistíte tím, že ovládací prvek bude nadále spouštět v případě <xref:System.Windows.Controls.ControlTemplate> chybí <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Použití VisualStateManager ke správě stavů  
 <xref:System.Windows.VisualStateManager> Uchovává informace o stavu ovládacího prvku a provádějí logiku potřebnou pro přechod mezi stavy. Když přidáte <xref:System.Windows.VisualState> objektů <xref:System.Windows.Controls.ControlTemplate>, přidejte je do <xref:System.Windows.VisualStateGroup> a přidejte <xref:System.Windows.VisualStateGroup> k <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost tak, aby <xref:System.Windows.VisualStateManager> k nim má přístup.  
  
 V následujícím příkladu se opakuje předchozí příklad, který ukazuje <xref:System.Windows.VisualState> objekty, které odpovídá `Positive` a `Negative` stavy ovládacího prvku. <xref:System.Windows.Media.Animation.Storyboard> v `Negative` <xref:System.Windows.VisualState> se změní <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> červené.   Při `NumericUpDown` ovládací prvek je v `Negative` scénář ve stavu `Negative` začíná stavu.  Pak bude <xref:System.Windows.Media.Animation.Storyboard> v `Negative` stavu zastaví, když se ovládací prvek vrátí `Positive` stavu.  `Positive` <xref:System.Windows.VisualState> Nemusí obsahovat <xref:System.Windows.Media.Animation.Storyboard> vzhledem k tomu, když <xref:System.Windows.Media.Animation.Storyboard> pro `Negative` zastaví, <xref:System.Windows.Controls.TextBlock.Foreground%2A> vrátí původní barvu.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Všimněte si, že <xref:System.Windows.Controls.TextBlock> je přiřazen název, ale <xref:System.Windows.Controls.TextBlock> se nenachází v kontrakt ovládacího prvku pro `NumericUpDown` protože logiky ovládacího prvku nikdy odkazuje <xref:System.Windows.Controls.TextBlock>.  Prvky, které jsou odkazovány v <xref:System.Windows.Controls.ControlTemplate> mít názvy, ale nemusí být součástí kontrakt ovládacího prvku, protože nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek nemusí odkazovat na tento element.  Například tím, kdo vytváří nový <xref:System.Windows.Controls.ControlTemplate> pro `NumericUpDown` není označuje, že se rozhodnout `Value` je záporný tak, že změníte <xref:System.Windows.Controls.Control.Foreground%2A>.  V takovém případě žádný kód ani <xref:System.Windows.Controls.ControlTemplate> odkazy <xref:System.Windows.Controls.TextBlock> podle názvu.  
  
 Logiky ovládacího prvku je zodpovědná za změnu stavu ovládacího prvku. Následující příklad ukazuje, že `NumericUpDown` řídit volání <xref:System.Windows.VisualStateManager.GoToState%2A> metoda přejde do `Positive` stav, kdy `Value` je 0 nebo větší a `Negative` stav, kdy `Value` je menší než 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Metoda provádí logiku potřebnou ke spuštění a zastavení scénáře odpovídajícím způsobem. Když ovládacího prvku volá <xref:System.Windows.VisualStateManager.GoToState%2A> změnit její stav <xref:System.Windows.VisualStateManager> provede následující akce:  
  
-   Pokud <xref:System.Windows.VisualState> , že se bude ovládací prvek má <xref:System.Windows.Media.Animation.Storyboard>, začne scénáři. Když se poté <xref:System.Windows.VisualState> pocházejí ovládací prvek má <xref:System.Windows.Media.Animation.Storyboard>, elementy end scénáře.  
  
-   Pokud je ovládací prvek ve stavu, který je zadán, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `true`.  
  
-   Pokud v neexistuje stav, který je zadán <xref:System.Windows.Controls.ControlTemplate> z `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Osvědčené postupy pro práci s VisualStateManager  
 Doporučujeme, abyste udělali následující Udržovat stavy ovládacího prvku:  
  
-   Pomocí vlastnosti můžete sledovat její stav.  
  
-   Vytvoření Pomocná metoda pro přechod mezi stavy.  
  
 `NumericUpDown` Používá ovládací prvek jeho `Value` vlastnost sleduje, zda se `Positive` nebo `Negative` stavu.  `NumericUpDown` Také definuje ovládací prvek `Focused` a `UnFocused` stavy, které sleduje <xref:System.Windows.UIElement.IsFocused%2A> vlastnost. Pokud používáte stavy, které neodpovídají přirozeně vlastnost ovládacího prvku, můžete definovat privátní vlastnosti, které chcete sledovat stav.  
  
 Jedinou metodu, která aktualizuje všechny stavy centralizuje volání <xref:System.Windows.VisualStateManager> a udržuje spravovat váš kód. Následující příklad ukazuje `NumericUpDown` ovládacího prvku Pomocná metoda `UpdateStates`. Když `Value` je větší než nebo rovno 0, <xref:System.Windows.Controls.Control> probíhá `Positive` stavu.  Když `Value` je menší než 0, ovládací prvek je `Negative` stavu.  Když <xref:System.Windows.UIElement.IsFocused%2A> je `true`, tento ovládací prvek `Focused` stavu; jinak, je v `Unfocused` stavu.  Ovládací prvek může volat `UpdateStates` vždy, když je potřeba změnit její stav, bez ohledu na to, jaký stav se změní.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Pokud předáte název stavu, který <xref:System.Windows.VisualStateManager.GoToState%2A> ovládací prvek je již v tomto stavu <xref:System.Windows.VisualStateManager.GoToState%2A> nemá žádný účinek, takže není nutné ke kontrole aktuální stav ovládacího prvku.  Například pokud `Value` změní z jedné záporné číslo na jiné záporné číslo, scénář pro `Negative` stavu proces se nepřerušil, a uživatel neuvidí změn v ovládacím prvku.  
  
 <xref:System.Windows.VisualStateManager> Používá <xref:System.Windows.VisualStateGroup> objekty k určení stavu, které pro ukončení při volání <xref:System.Windows.VisualStateManager.GoToState%2A>. Ovládací prvek je vždy v jednom ze stavů pro každou <xref:System.Windows.VisualStateGroup> , která je definována v jeho <xref:System.Windows.Controls.ControlTemplate> a pouze opustí stavu při přechodu do jiného státu ze stejné <xref:System.Windows.VisualStateGroup>. Například <xref:System.Windows.Controls.ControlTemplate> z `NumericUpDown` definuje ovládací prvek `Positive` a `Negative` <xref:System.Windows.VisualState> objektů v jednom <xref:System.Windows.VisualStateGroup> a `Focused` a `Unfocused` <xref:System.Windows.VisualState> objekty v jiném. (Můžete zobrazit `Focused` a `Unfocused` <xref:System.Windows.VisualState> definované v [kompletní příklad](#complete_example) v tomto tématu, když se ovládací prvek dostane od `Positive` do stavu `Negative` stavu, nebo naopak, ovládací prvek zůstane v buď `Focused` nebo `Unfocused` stavu.  
  
 Existují tři typické místa, kde může změnit stav ovládacího prvku:  
  
-   Když <xref:System.Windows.Controls.ControlTemplate> platí pro <xref:System.Windows.Controls.Control>.  
  
-   Když se změní vlastnost.  
  
-   Při výskytu události.  
  
 Následující příklady ukazují, aktualizuje se stav `NumericUpDown` ovládacího prvku v těchto případech.  
  
 Měli byste aktualizovat stav ovládacího prvku <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metoda tak, aby ovládací prvek zobrazil ve správné stav, kdy <xref:System.Windows.Controls.ControlTemplate> platí. Následující příklad volá `UpdateStates` v <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> tak, aby byl ovládací prvek v příslušné stavy.  Předpokládejme například, že vytvoříte `NumericUpDown` ovládací prvek a pak nastavte jeho <xref:System.Windows.Controls.Control.Foreground%2A> na zelenou a `Value` k -5.  Pokud není volána `UpdateStates` při <xref:System.Windows.Controls.ControlTemplate> platí pro `NumericUpDown` ovládací prvek, ovládací prvek není v `Negative` stavu a jeho hodnota je místo červená zelená.  Je nutné volat `UpdateStates` vložit ovládací prvek `Negative` stavu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Často je potřeba aktualizovat stav ovládacího prvku, když se změní vlastnost. Následující příklad ukazuje celý `ValueChangedCallback` metody. Protože `ValueChangedCallback` je volána, když `Value` změní, volání metod `UpdateStates` v případě, že `Value` změnil z kladné na zápornou nebo naopak. Je to přijatelné pro volání `UpdateStates` při `Value` změní, ale zůstává kladné nebo záporné, protože v takovém případě nebude ovládací prvek změnit stavy.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Potřebujete také aktualizovat stavy při výskytu události. Následující příklad ukazuje, že `NumericUpDown` volání `UpdateStates` na <xref:System.Windows.Controls.Control> ke zpracování <xref:System.Windows.UIElement.GotFocus> událostí.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Vám usnadní správu stavů ovládacího prvku. S použitím <xref:System.Windows.VisualStateManager>, zajistíte tím, že ovládací prvek správně přechody mezi stavy.  Pokud budete postupovat podle doporučení popsané v této části pro práci s <xref:System.Windows.VisualStateManager>, ovládacího prvku kód zůstane čitelný a udržovatelný.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Poskytuje kontrakt ovládacího prvku  
 Zadejte kontrakt ovládacího prvku tak, aby <xref:System.Windows.Controls.ControlTemplate> autoři vědět, co vložit v šabloně. Kontrakt ovládacího prvku má tři prvky:  
  
-   Vizuální prvky, které používá logiky ovládacího prvku.  
  
-   Stavy ovládacího prvku a skupiny, do které patří každý stav.  
  
-   Veřejné vlastnosti, které ovlivňují vizuální ovládací prvek.  
  
 Uživatel, který vytvoří nový <xref:System.Windows.Controls.ControlTemplate> potřebuje vědět, co <xref:System.Windows.FrameworkElement> objekty ovládacího prvku logika více cest použije, jaký typ každý objekt je a zadejte jeho název je. A <xref:System.Windows.Controls.ControlTemplate> Autor také potřeba znát název jednotlivých možných stavech ovládací prvek může být v a které <xref:System.Windows.VisualStateGroup> stav není v.  
  
 Vrácení `NumericUpDown` očekává, že například ovládací prvek <xref:System.Windows.Controls.ControlTemplate> mít následující <xref:System.Windows.FrameworkElement> objekty:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> volá `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> volá `DownButton.`  
  
 Ovládací prvek může být v následujících stavů:  
  
-   V `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   V `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Chcete-li určit, co <xref:System.Windows.FrameworkElement> očekává, že objekty ovládacího prvku, je použít <xref:System.Windows.TemplatePartAttribute>, který určuje název a typ očekávané prvky.  Chcete-li určit možné stavy ovládacího prvku, použijete <xref:System.Windows.TemplateVisualStateAttribute>, který určuje název stavu a která <xref:System.Windows.VisualStateGroup> patří do.  Vložit <xref:System.Windows.TemplatePartAttribute> a <xref:System.Windows.TemplateVisualStateAttribute> na definici třídy ovládacího prvku.  
  
 Veřejná vlastnost, která má vliv na vzhled ovládacího prvku je také součástí kontrakt ovládacího prvku.  
  
 V následujícím příkladu <xref:System.Windows.FrameworkElement> objektu a stavy `NumericUpDown` ovládacího prvku.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletní příklad  
 V následujícím příkladu je celý <xref:System.Windows.Controls.ControlTemplate> pro `NumericUpDown` ovládacího prvku.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 Následující příklad ukazuje logiku pro `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Viz také:
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
- [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
