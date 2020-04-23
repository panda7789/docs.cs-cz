---
title: Vytvoření stylu ovládacího prvku
description: Zjistěte, jak vytvořit a odkazovat na styl ovládacího prvku v systému Windows Presentation Foundation a .NET Core.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071267"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Vytvoření stylu ovládacího prvku ve WPF

Pomocí služby Windows Presentation Foundation (WPF) můžete přizpůsobit vzhled existujícího ovládacího prvku pomocí vlastního opakovaně použitelného stylu. Styly lze použít globálně na vaši aplikaci, okna a stránky nebo přímo na ovládací prvky.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Vytvoření stylu

Můžete si <xref:System.Windows.Style> myslet, že je vhodný způsob, jak použít sadu hodnot vlastností na jeden nebo více prvků. Styl můžete použít na libovolný prvek, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> který je <xref:System.Windows.Window> odvozen <xref:System.Windows.Controls.Button>od nebo například nebo .

Nejběžnější způsob deklarování stylu je jako `Resources` prostředek v části v souboru XAML. Vzhledem k tomu, že styly jsou prostředky, řídí se stejnými pravidly oboru, která platí pro všechny prostředky. Jednoduše řečeno, kde deklarujete styl ovlivňuje, kde lze použít styl. Pokud například deklarujete styl v kořenovém prvku souboru XAML definice aplikace, styl lze použít kdekoli ve vaší aplikaci.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Pokud deklarujete styl v jednom ze souborů XAML aplikace, styl lze použít pouze v tomto souboru XAML. Další informace o oboru pravidla pro prostředky naleznete v tématu [XAML prostředky](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Styl se skládá `<Setter>` z podřízených prvků, které nastavují vlastnosti prvků, na které je styl aplikován. Ve výše uvedeném příkladu si všimněte, že styl je nastaven tak, aby se vztahoval na `TextBlock` typy prostřednictvím atributu. `TargetType` Styl nastaví <xref:System.Windows.Controls.Control.FontSize%2A> na `15` a <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold`na . Přidejte `<Setter>` pro každou vlastnost změny stylu.

## <a name="apply-a-style-implicitly"></a>Implicitní použití stylu

A <xref:System.Windows.Style> je pohodlný způsob, jak použít sadu hodnot vlastností na více než jeden prvek. Zvažte například <xref:System.Windows.Controls.TextBlock> následující prvky a jejich výchozí vzhled v okně.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Ukázkový snímek obrazovky s stylingem](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Výchozí vzhled můžete změnit nastavením vlastností, například <xref:System.Windows.Controls.Control.FontSize%2A> a <xref:System.Windows.Controls.Control.FontFamily%2A>, u každého <xref:System.Windows.Controls.TextBlock> prvku přímo. Pokud však chcete, aby prvky <xref:System.Windows.Controls.TextBlock> sdílely <xref:System.Windows.Style> některé `Resources` vlastnosti, můžete vytvořit v části souboru XAML, jak je znázorněno zde.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Když <xref:System.Windows.Style.TargetType%2A> nastavíte styl na <xref:System.Windows.Controls.TextBlock> typ a vyneche `x:Key` atribut, styl <xref:System.Windows.Controls.TextBlock> se použije na všechny prvky, které jsou vymezeny stylem, což je obecně samotný soubor XAML.

Nyní <xref:System.Windows.Controls.TextBlock> se prvky zobrazují následovně.

![Ukázkový snímek obrazovky s stylingem](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Explicitní použití stylu

Pokud přidáte `x:Key` atribut s hodnotou do stylu, styl již není implicitně aplikován na všechny prvky aplikace <xref:System.Windows.Style.TargetType%2A>. Pouze prvky, které explicitně odkazují na styl, budou mít styl použitý na ně.

Zde je styl z předchozí části, `x:Key` ale deklarován s atributem.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Chcete-li použít styl, nastavte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost `x:Key` na prvek na hodnotu pomocí [rozšíření značky StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), jak je znázorněno zde.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Všimněte si, že první <xref:System.Windows.Controls.TextBlock> prvek má styl použít, zatímco druhý TextBlock prvek zůstane beze změny. Implicitní styl z předchozí části byl změněn `x:Key` na styl, který deklaroval atribut, což znamená, že jediný prvek ovlivněný stylem je ten, který přímo odkazoval na styl.

![Ukázkový snímek obrazovky s stylingem](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "vytvořit -a-style-explicit-textblock")

Jakmile je styl použit, explicitně nebo implicitně, stane se zapečetěným a nelze jej změnit. Pokud chcete změnit styl, který byl použit, vytvořte nový styl, který nahradí stávající styl. Další informace naleznete <xref:System.Windows.Style.IsSealed%2A> v ubytovacím zařízení.

Můžete vytvořit objekt, který zvolí styl použít na základě vlastní logiky. Příklad naleznete v příkladu pro <xref:System.Windows.Controls.StyleSelector> třídu.

## <a name="apply-a-style-programmatically"></a>Programové použití stylu

Chcete-li prvek udělit pojmenovaný styl programově, získejte jej z kolekce prostředků <xref:System.Windows.FrameworkElement.Style%2A> a přiřaďte jej k vlastnosti prvku. Položky v kolekci prostředků <xref:System.Object>jsou typu . Proto je nutné přetypovat načtený styl <xref:System.Windows.Style?displayProperty=fullName> před `Style` přiřazením k vlastnosti. Například následující kód nastaví styl `TextBlock` `textblock1` pojmenovaného definovaného stylu `TitleText`.

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Rozšíření stylu

Možná chcete, <xref:System.Windows.Controls.TextBlock> aby vaše dva prvky sdílet <xref:System.Windows.Controls.Control.FontFamily%2A> některé hodnoty <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>vlastností, jako je například a na střed . Chcete však také, aby text **Moje obrázky** měl některé další vlastnosti. Můžete to udělat vytvořením nového stylu, který je založen na prvním stylu, jak je znázorněno zde.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Tento `TextBlock` styl je nyní vystředěný, používá `Comic Sans MS` písmo o velikosti `26`a barvu popředí nastavenou na barvu uvedenou <xref:System.Windows.Media.LinearGradientBrush> v příkladu. Všimněte si, <xref:System.Windows.Controls.Control.FontSize%2A> že přepíše hodnotu základního stylu. Pokud je více než <xref:System.Windows.Setter> jeden ukazující na <xref:System.Windows.Style>stejnou `Setter` vlastnost v , který je deklarován poslední má přednost.

Následující ukazuje, <xref:System.Windows.Controls.TextBlock> jak prvky nyní vypadají:

![Stylizované textové bloky](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Tento `TitleText` styl rozšiřuje styl, který byl <xref:System.Windows.Controls.TextBlock> vytvořen pro `BasedOn="{StaticResource {x:Type TextBlock}}"`typ, na který odkazuje . Můžete také rozšířit styl, `x:Key` který má `x:Key` pomocí stylu. Pokud byl například pojmenován `Header1` styl a vy jste chtěli `BasedOn="{StaticResource Header1}"`tento styl rozšířit, použili byste .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Vztah vlastnosti TargetType a atributu x:Key

Jak již bylo <xref:System.Windows.Style.TargetType%2A> ukázáno `TextBlock` dříve, nastavení `x:Key` vlastnosti bez přiřazení stylu <xref:System.Windows.Controls.TextBlock> způsobí, že styl bude použit na všechny prvky. V tomto případě `x:Key` je implicitně `{x:Type TextBlock}`nastavena na . To znamená, že pokud `x:Key` explicitně nastavíte <xref:System.Windows.Style> hodnotu na `TextBlock` cokoli jiného než `{x:Type TextBlock}`, nebude automaticky použita na všechny prvky. Místo toho je nutné použít styl `x:Key` (pomocí `TextBlock` hodnoty) na prvky explicitně. Pokud je váš styl v části zdroje a `TargetType` nenastavíte vlastnost na `x:Key` váš styl, musíte nastavit atribut.

Kromě poskytnutí výchozí hodnoty pro `x:Key`, `TargetType` vlastnost určuje typ, na který se vztahují vlastnosti nastavení. Pokud nezadáte `TargetType`, musíte vlastnosti v <xref:System.Windows.Setter> objektech kvalifikovat pomocí názvu `Property="ClassName.Property"`třídy pomocí syntaxe . Například místo nastavení `Property="FontSize"`je nutné <xref:System.Windows.Setter.Property%2A> `"TextBlock.FontSize"` nastavit `"Control.FontSize"`nebo .

Všimněte si také, že mnoho ovládacích prvků WPF se skládá z kombinace jiných ovládacích prvků WPF. Pokud vytvoříte styl, který se vztahuje na všechny ovládací prvky typu, může dojít k neočekávaným výsledkům. Pokud například vytvoříte styl, <xref:System.Windows.Controls.TextBlock> který cílí na typ <xref:System.Windows.Window>v `TextBlock` aplikaci , bude `TextBlock` styl použit na všechny ovládací <xref:System.Windows.Controls.ListBox>prvky v okně, a to i v případě, že je součástí jiného ovládacího prvku, například .

## <a name="see-also"></a>Viz také

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Přehled zdrojů XAML](xaml-resources-define.md)
- [Přehled XAML (WPF & .NET Core)](xaml.md)
