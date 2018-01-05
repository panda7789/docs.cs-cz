---
title: "Vytvoření ovládacího prvku se vzhledem, který lze přizpůsobit"
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
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4da96c3e33c6f7827619b408568fbbfe96c50a11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Vytvoření ovládacího prvku se vzhledem, který lze přizpůsobit
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]vám dává možnost vytvořit ovládací prvek, jejichž vzhled lze přizpůsobit. Například můžete změnit vzhled <xref:System.Windows.Controls.CheckBox> nad rámec jaká nastavení vlastnosti provede vytvořením nového <xref:System.Windows.Controls.ControlTemplate>. Následující obrázek znázorňuje <xref:System.Windows.Controls.CheckBox> používající výchozí <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.CheckBox> používající vlastní <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Zaškrtávací políčko s výchozí šablony ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaškrtávací políčko, který používá výchozí šablonu pro ovládací prvek  
  
 ![Zaškrtávací políčko se šablonou vlastního ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaškrtávací políčko, který používá šablonu vlastního ovládacího prvku  
  
 Pokud budete postupovat podle modelu částí a stavy při vytvoření ovládacího prvku, bude lze přizpůsobit vzhled ovládacího prvku. Návrhářské nástroje, jako je například Microsoft Expression Blend díky podpoře částí a stavů modelu, pokud budete postupovat podle tohoto modelu vlastní ovládací prvek bude přizpůsobitelné v těchto typech aplikací.  Toto téma popisuje částí a stavů modelu a postupujte podle při vytvoření vlastního ovládacího prvku. Toto téma používá příklad vlastního ovládacího prvku, `NumericUpDown`, k objasnění filosofie tohoto modelu.  `NumericUpDown` Zobrazí číselnou hodnotu, která uživatele můžete zvýšit nebo snížit kliknutím na tlačítka ovládacího prvku.  Následující obrázek ukazuje `NumericUpDown` ovládací prvek, který je popsané v tomto tématu.  
  
 ![NumericUpDown vlastního ovládacího prvku. ] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
Vlastního ovládacího prvku NumericUpDown  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Požadavky](#prerequisites)  
  
-   [Části a stavů modelu](#parts_and_states_model)  
  
-   [Definování Visual strukturu a Visual chování ovládacího prvku v ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Použití části ControlTemplate v kódu](#using_parts_of_the_controltemplate_in_code)  
  
-   [Poskytnutí kontrakt ovládací prvek](#providing_the_control_contract)  
  
-   [Úplný příklad](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že víte, jak vytvořit nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek existující obeznámeni s co jsou elementy na kontraktu řízení a pochopit principy probírané v [přizpůsobení vzhledu ovládacího prvku existující podle Vytváření ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Vytvoření ovládacího prvku, který může mít její vzhled přizpůsobit, musíte vytvořit ovládacího prvku, který dědí z <xref:System.Windows.Controls.Control> třídu nebo jeden z jeho podtřídy jinak než <xref:System.Windows.Controls.UserControl>.  Ovládací prvek, který dědí z <xref:System.Windows.Controls.UserControl> je ovládací prvek, který lze rychle vytvořit, ale nepoužívá <xref:System.Windows.Controls.ControlTemplate> a nelze přizpůsobit její vzhled.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Části a stavů modelu  
 Model částí a stavy Určuje, jak definovat visual strukturu a visual chování ovládacího prvku. Dodržet model částí a stavy, měli byste udělat následující:  
  
-   Definování visual struktura a visual chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku.  
  
-   Postupujte podle některé osvědčené postupy při ovládacího prvku logiku interakci s částmi šablonu ovládacího prvku.  
  
-   Zadejte kontraktu řízení k určení, co by měl být součástí <xref:System.Windows.Controls.ControlTemplate>.  
  
 Když definujete visual strukturu a visual chování v <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku autoři aplikace můžete změnit visual strukturu a visual chování ovládacího prvku tak, že vytvoříte novou <xref:System.Windows.Controls.ControlTemplate> místo psaní kódu.   Je nutné zadat vytvoří kontraktu ovládacího prvku s informacemi o aplikaci, která <xref:System.Windows.FrameworkElement> objekty a stavy je nutné definovat v <xref:System.Windows.Controls.ControlTemplate>. Pokud při práci s částí v některé z osvědčených postupů postupujte <xref:System.Windows.Controls.ControlTemplate> tak, aby vlastní ovládací prvek správně zpracovává neúplnou <xref:System.Windows.Controls.ControlTemplate>.  Pokud budete postupovat podle těchto tří zásad, autoři aplikace budou moci vytvořit <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek jenom jako jejich snadno můžete pro ovládací prvky, dodávají spolu s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Následující část popisuje každý z těchto doporučení podrobně.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definování Visual strukturu a Visual chování ovládacího prvku v ControlTemplate  
 Když vytvoříte vlastního ovládacího prvku pomocí modelu částí a stavy, definujete ovládacího prvku visual strukturu a visual chování v jeho <xref:System.Windows.Controls.ControlTemplate> místo svou logikou.  Vizuální strukturu ovládacího prvku je složený z <xref:System.Windows.FrameworkElement> objekty, které tvoří ovládacího prvku.  Visual chování je způsob, jakým ovládacího prvku se zobrazí, když je v určitých stavu.   Další informace o vytváření <xref:System.Windows.Controls.ControlTemplate> určující visual strukturu a visual chování ovládacího prvku najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 V příkladu `NumericUpDown` řízení, visual struktura zahrnuje dvě <xref:System.Windows.Controls.Primitives.RepeatButton> ovládací prvky a <xref:System.Windows.Controls.TextBlock>.  Pokud přidáte tyto ovládací prvky v kódu `NumericUpDown` řízení--v jeho konstruktoru, například polohy kontrolní mechanismy by změnit.  Místo definování visual struktura a visual chování ovládacího prvku v jeho kódu, byste měli definovat v <xref:System.Windows.Controls.ControlTemplate>.  Potom vývojář aplikace k přizpůsobení pozici tlačítek a <xref:System.Windows.Controls.TextBlock> a určete, jaké chování dochází při `Value` je záporná. protože <xref:System.Windows.Controls.ControlTemplate> lze nahradit.  
  
 Následující příklad ukazuje visual strukturu `NumericUpDown` řízení, které zahrnuje <xref:System.Windows.Controls.Primitives.RepeatButton> zvýšit `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> snížení `Value`a <xref:System.Windows.Controls.TextBlock> zobrazíte `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Visual chování `NumericUpDown` ovládací prvek je, že hodnota je red písmeny, pokud je záporná.  Pokud změníte <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> v kódu při `Value` záporná, `NumericUpDown` bude vždy zobrazovat red zápornou hodnotu. Zadejte visual chování ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> přidáním <xref:System.Windows.VisualState> objekty ke <xref:System.Windows.Controls.ControlTemplate>.  Následující příklad ukazuje <xref:System.Windows.VisualState> pro objekty `Positive` a `Negative` stavy.  `Positive`a `Negative` se vzájemně vylučují (ovládací prvek, je vždy přesně jednu ze dvou), takže v příkladu umístí <xref:System.Windows.VisualState> objekty do jednoho <xref:System.Windows.VisualStateGroup>.  Pokud ovládací prvek přejde do `Negative` stavu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> na červenou.  Pokud ovládací prvek, je `Positive` stavu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> vrátí k němu původní hodnotu.  Definování <xref:System.Windows.VisualState> objekty v <xref:System.Windows.Controls.ControlTemplate> další popsané v [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Nastavte <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost v kořenovém <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Použití části ControlTemplate v kódu  
 A <xref:System.Windows.Controls.ControlTemplate> může vynechat Autor <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState> objekty, záměrně nebo omylem, ale logiku ovládacího prvku může být třeba tyto části fungovat správně. Model částí a stavy Určuje, že vlastního ovládacího prvku by měl být odolné vůči <xref:System.Windows.Controls.ControlTemplate> , kde chybí <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.VisualState> objekty.  Vlastní ovládací prvek by neměl vyvolá výjimku nebo sestava chybu, pokud <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, nebo <xref:System.Windows.VisualStateGroup> chybí <xref:System.Windows.Controls.ControlTemplate>. Tato část popisuje doporučené postupy pro interakci s <xref:System.Windows.FrameworkElement> objektů a správa stavů.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Předvídat chybějící FrameworkElement objekty  
 Když definujete <xref:System.Windows.FrameworkElement> objekty v <xref:System.Windows.Controls.ControlTemplate>, k interakci se některá z nich může být nutné logiku ovládacího prvku.  Například `NumericUpDown` ovládací prvek jako odběratel u příslušných tlačítek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí zvýšení nebo snížení `Value` a nastaví <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost <xref:System.Windows.Controls.TextBlock> k `Value`. Pokud vlastní <xref:System.Windows.Controls.ControlTemplate> vynechá <xref:System.Windows.Controls.TextBlock> nebo tlačítka, je přijatelné, že daný ovládací prvek již některé ze svých funkcí, ale byste měli jistotu, že vlastní ovládací prvek není způsobit chybu. Například pokud <xref:System.Windows.Controls.ControlTemplate> neobsahuje tlačítka Změnit `Value`, `NumericUpDown` ztratí, které tuto funkci, ale aplikace, která používá <xref:System.Windows.Controls.ControlTemplate> bude nadále spouštět.  
  
 Následující postupy zajistí správně odpoví vlastního ovládacího prvku k chybějící <xref:System.Windows.FrameworkElement> objekty:  
  
1.  Nastavte `x:Name` atribut pro každý <xref:System.Windows.FrameworkElement> , které potřebujete k odkazujete v kódu.  
  
2.  Definovat privátní vlastnosti pro každou <xref:System.Windows.FrameworkElement> , které potřebujete k interakci s.  
  
3.  Přihlášení a odhlášení ze všech událostí, které vlastní ovládací prvek zpracovává v <xref:System.Windows.FrameworkElement> sadu přistupujícího objektu vlastnosti.  
  
4.  Nastavte <xref:System.Windows.FrameworkElement> vlastnosti, které jste zadali v kroku 2 v <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metoda. Toto je první, <xref:System.Windows.FrameworkElement> v <xref:System.Windows.Controls.ControlTemplate> je k dispozici do ovládacího prvku. Použití `x:Name` z <xref:System.Windows.FrameworkElement> získat z <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Zkontrolujte, zda <xref:System.Windows.FrameworkElement> není `null` před přístupem k její členy.  Pokud je `null`, Neoznamovat k chybě.  
  
 Následující příklady zobrazují jak `NumericUpDown` řízení komunikuje s <xref:System.Windows.FrameworkElement> objekty podle doporučení v předchozím seznamu.  
  
 V příkladu, který definuje visual strukturu `NumericUpDown` řídit ve <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> , zvyšuje `Value` má jeho `x:Name` atribut nastaven na `UpButton`.  Následující příklad deklaruje vlastnost s názvem `UpButtonElement` představující <xref:System.Windows.Controls.Primitives.RepeatButton> deklarovaného v souboru <xref:System.Windows.Controls.ControlTemplate>. `set` Přistupujícího objektu odhlášení odběrů nejprve na tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí Pokud `UpDownElement` není `null`, potom nastaví vlastnost a potom se přihlásí k odběru <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. Je také vlastnost definovaná, ale není tady, zobrazené pro druhý <xref:System.Windows.Controls.Primitives.RepeatButton>, názvem `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 Následující příklad ukazuje <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pro `NumericUpDown` ovládacího prvku.  V příkladu se používá <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metoda získat <xref:System.Windows.FrameworkElement> objekty z <xref:System.Windows.Controls.ControlTemplate>.  Všimněte si, že v příkladu chrání před případech, kdy <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> vyhledá <xref:System.Windows.FrameworkElement> se zadaným názvem, který není očekávaného typu. Je také vhodné ignorovat prvky, které mají zadaný `x:Name` , ale jsou nesprávného typu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Pomocí následujících postupů, které jsou zobrazeny v předchozích příkladech, zajistíte, že bude nadále spouštět v případě vlastního ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> chybí <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Použití VisualStateManager ke správě stavy  
 <xref:System.Windows.VisualStateManager> Sleduje stav ovládacího prvku a provede nezbytné pro přechod mezi stavy logiku. Když přidáte <xref:System.Windows.VisualState> objekty ke <xref:System.Windows.Controls.ControlTemplate>, přidat je do <xref:System.Windows.VisualStateGroup> a přidejte <xref:System.Windows.VisualStateGroup> k <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> přidružená vlastnost tak, aby <xref:System.Windows.VisualStateManager> má přístup k nim.  
  
 V následujícím příkladu se opakuje předchozí příklad, který ukazuje <xref:System.Windows.VisualState> objekty, které odpovídá `Positive` a `Negative` stavy ovládacího prvku. <xref:System.Windows.Media.Animation.Storyboard> v `Negative` <xref:System.Windows.VisualState> se změní <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> red.   Při `NumericUpDown` ovládací prvek nachází `Negative` stavu storyboard v `Negative` začne stavu.  Pak se <xref:System.Windows.Media.Animation.Storyboard> v `Negative` stavu zastaví, když se vrátí ovládací prvek `Positive` stavu.  `Positive` <xref:System.Windows.VisualState> Nemusí obsahovat <xref:System.Windows.Media.Animation.Storyboard> vzhledem k tomu, když <xref:System.Windows.Media.Animation.Storyboard> pro `Negative` zastaví, <xref:System.Windows.Controls.TextBlock.Foreground%2A> vrátí původní barvu.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Všimněte si, že <xref:System.Windows.Controls.TextBlock> je zadaný název, ale <xref:System.Windows.Controls.TextBlock> není v řízení kontrakt `NumericUpDown` protože ovládacího prvku logiku nikdy odkazuje <xref:System.Windows.Controls.TextBlock>.  Elementy, které odkazují <xref:System.Windows.Controls.ControlTemplate> mít názvy, ale nemusí být součástí kontraktu ovládacího prvku, protože nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek nemusí. Chcete-li daný element.  Například někoho, kdo vytvoří novou <xref:System.Windows.Controls.ControlTemplate> pro `NumericUpDown` může rozhodnout, že není označuje, že `Value` , je záporná změna <xref:System.Windows.Controls.Control.Foreground%2A>.  V takovém případě ani kód ani <xref:System.Windows.Controls.ControlTemplate> odkazy <xref:System.Windows.Controls.TextBlock> podle názvu.  
  
 Pro změnu stavu ovládacího prvku zodpovídá logiku ovládacího prvku. Následující příklad ukazuje, že `NumericUpDown` řízení volání <xref:System.Windows.VisualStateManager.GoToState%2A> metoda přejdete do `Positive` stavu, kdy `Value` je 0 nebo větší a `Negative` stavu, kdy `Value` je menší než 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Metoda provádí logice nezbytné pro spuštění a zastavení scénářů správně. Při volání ovládacího prvku <xref:System.Windows.VisualStateManager.GoToState%2A> změny jeho stavu <xref:System.Windows.VisualStateManager> provede následující akce:  
  
-   Pokud <xref:System.Windows.VisualState> , že se bude ovládací prvek má <xref:System.Windows.Media.Animation.Storyboard>, začne scénáři. Poté, pokud <xref:System.Windows.VisualState> jestli ovládacího prvku pochází z má <xref:System.Windows.Media.Animation.Storyboard>, skončení scénáře.  
  
-   Pokud ovládací prvek je již ve stavu, který je zadán, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `true`.  
  
-   Pokud v neexistuje stav, který je zadaný <xref:System.Windows.Controls.ControlTemplate> z `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci a vrátí `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Osvědčené postupy pro práci s VisualStateManager  
 Doporučujeme, abyste provedli následující příkaz pro udržování stavu ovládacího prvku:  
  
-   Pomocí vlastností sledovat jeho stav.  
  
-   Vytvořte Pomocná metoda pro přechod mezi stavy.  
  
 `NumericUpDown` Řízení používá jeho `Value` vlastnost sleduje, zda je v `Positive` nebo `Negative` stavu.  `NumericUpDown` Ovládací prvek také definuje `Focused` a `UnFocused` stavy, které sleduje <xref:System.Windows.UIElement.IsFocused%2A> vlastnost. Pokud používáte stavy, které neodpovídají přirozeně vlastností ovládacího prvku, můžete definovat privátní vlastnost ke sledování stavu.  
  
 Jedinou metodu, která aktualizuje všechny stavy centralizuje volání <xref:System.Windows.VisualStateManager> a udržuje spravovat váš kód. Následující příklad ukazuje `NumericUpDown` ovládacího prvku Pomocná metoda, `UpdateStates`. Když `Value` je větší než nebo rovno 0, <xref:System.Windows.Controls.Control> v `Positive` stavu.  Když `Value` je menší než 0, ovládací prvek, je `Negative` stavu.  Když <xref:System.Windows.UIElement.IsFocused%2A> je `true`, ovládací prvek, je `Focused` stavu; jinak hodnota, je v `Unfocused` stavu.  Ovládací prvek můžete volat `UpdateStates` vždy, když je potřeba změnit její stav, bez ohledu na to, jaký stav se změní.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Pokud předáte název stavu, který <xref:System.Windows.VisualStateManager.GoToState%2A> Pokud ovládací prvek je již v tomto stavu <xref:System.Windows.VisualStateManager.GoToState%2A> neprovede žádnou akci, takže není nutné zkontrolujte aktuální stav ovládacího prvku.  Například pokud `Value` z jednoho záporná čísla se změní na jiné záporné číslo, scénáře pro `Negative` proces se nepřerušil stavu a uživatel nebude vidět změnu v ovládacím prvku.  
  
 <xref:System.Windows.VisualStateManager> Používá <xref:System.Windows.VisualStateGroup> objekty, které chcete určit, které stavu ukončíte při volání <xref:System.Windows.VisualStateManager.GoToState%2A>. Ovládací prvek, je vždy jeden stav pro každý <xref:System.Windows.VisualStateGroup> která je definovaná v jeho <xref:System.Windows.Controls.ControlTemplate> a při přechodu do jiné stavu ze stejné pouze zůstane stavu <xref:System.Windows.VisualStateGroup>. Například <xref:System.Windows.Controls.ControlTemplate> z `NumericUpDown` definuje ovládacího prvku `Positive` a `Negative` <xref:System.Windows.VisualState> objektů v jednom <xref:System.Windows.VisualStateGroup> a `Focused` a `Unfocused` <xref:System.Windows.VisualState> objekty v jiném. (Můžete zobrazit `Focused` a `Unfocused` <xref:System.Windows.VisualState> definované v [kompletní příklad](#complete_example) v tomto tématu, kdy přestane ovládací prvek z `Positive` stavu na `Negative` stavu, nebo naopak, ovládací prvek zůstane buď `Focused` nebo `Unfocused` stavu.  
  
 Existují tři typické místa, kde může změnit stav kontroly:  
  
-   Když <xref:System.Windows.Controls.ControlTemplate> se použije na <xref:System.Windows.Controls.Control>.  
  
-   Když se změní vlastnost.  
  
-   Když dojde k události.  
  
 Následující příklady ukazují aktualizaci stavu `NumericUpDown` ovládací prvek v těchto případech.  
  
 By měl aktualizovat stav ovládacího prvku <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metoda tak, aby ovládací prvek se zobrazuje ve správné stavu, kdy <xref:System.Windows.Controls.ControlTemplate> platí. Následující příklad volání `UpdateStates` v <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> zajistit, že je ovládací prvek v příslušné stavy.  Předpokládejme například, že vytvoříte `NumericUpDown` řízení a poté nastavte její <xref:System.Windows.Controls.Control.Foreground%2A> na zelenou a `Value` na -5.  Pokud Nevolejte `UpdateStates` při <xref:System.Windows.Controls.ControlTemplate> se použije na `NumericUpDown` ovládací prvek, ovládací prvek není součástí `Negative` stavu a hodnota je zelená místo red.  Je třeba volat `UpdateStates` uvést do ovládacího prvku `Negative` stavu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Často je potřeba aktualizovat stavy ovládacího prvku při změně vlastnosti. Následující příklad ukazuje celý `ValueChangedCallback` metoda. Protože `ValueChangedCallback` je volána, když `Value` změní, volání metod `UpdateStates` v případě, že `Value` se změnil z pozitivní na záporné a naopak. Je přijatelné pro volání `UpdateStates` při `Value` změny, ale zůstává kladné a záporné, protože v takovém případě ovládacího prvku nedojde ke změně stavu.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Může také musíte aktualizovat stavy, když dojde k události. Následující příklad ukazuje, že `NumericUpDown` volání `UpdateStates` na <xref:System.Windows.Controls.Control> pro zpracování <xref:System.Windows.UIElement.GotFocus> událostí.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Vám pomůže spravovat stavy ovládacího prvku. Pomocí <xref:System.Windows.VisualStateManager>, zajistíte, že vlastní ovládací prvek správně přechody mezi stavy.  Pokud jste postupujte podle doporučení popsaných v této části pro práci s <xref:System.Windows.VisualStateManager>, vaše řídicí kód zůstane čitelný a udržovatelný.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Poskytnutí kontrakt ovládací prvek  
 Zadejte kontraktu ovládacího prvku tak, aby <xref:System.Windows.Controls.ControlTemplate> autoři věděli, co chcete umístit do šablony. Ovládací prvek kontrakt má tři prvky:  
  
-   Vizuální prvky, které používá logiku ovládacího prvku.  
  
-   Stavy ovládacího prvku a skupiny, ke které patří každý stav.  
  
-   Veřejné vlastnosti vizuálně ovlivňující ovládacího prvku.  
  
 Uživatel, který vytvoří nový <xref:System.Windows.Controls.ControlTemplate> musí vědět, co <xref:System.Windows.FrameworkElement> objekty používá logiku ovládacího prvku, co typ každého objektu je a jaké její název. A <xref:System.Windows.Controls.ControlTemplate> Autor také musí znát název všechny možné stavy ovládací prvek může být v a které <xref:System.Windows.VisualStateGroup> tento stav.  
  
 Vrácením `NumericUpDown` například očekává ovládacího prvku <xref:System.Windows.Controls.ControlTemplate> do mají následující <xref:System.Windows.FrameworkElement> objekty:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> názvem `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> názvem`DownButton.`  
  
 Ovládací prvek může být v následujících stavů:  
  
-   V`ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   V`FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Chcete-li určit, co <xref:System.Windows.FrameworkElement> očekává objekty ovládací prvek, je použít <xref:System.Windows.TemplatePartAttribute>, která určuje název a typ očekávaný elementů.  Chcete-li určit možné stavy ovládacího prvku, je použít <xref:System.Windows.TemplateVisualStateAttribute>, která určuje název stavu a které <xref:System.Windows.VisualStateGroup> patří do.  Umístit <xref:System.Windows.TemplatePartAttribute> a <xref:System.Windows.TemplateVisualStateAttribute> v definici třídy ovládacího prvku.  
  
 Všechny veřejné vlastnosti, která ovlivňuje vzhled ovládacího prvku je také součástí kontraktu ovládacího prvku.  
  
 Následující příklad určuje <xref:System.Windows.FrameworkElement> objekt a stavy `NumericUpDown` ovládacího prvku.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletní příklad  
 Následující příklad je celý <xref:System.Windows.Controls.ControlTemplate> pro `NumericUpDown` ovládacího prvku.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 Následující příklad ukazuje logiku pro `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
