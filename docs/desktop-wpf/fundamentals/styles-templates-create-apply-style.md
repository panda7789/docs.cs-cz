---
title: Vytvoření stylu pro ovládací prvek
description: Naučte se, jak vytvořit a odkazovat na styl ovládacího prvku v Windows Presentation Foundation a .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: de186cd6da83ffef8a5cd59df581e88b24bc474d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325795"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Vytvoření stylu pro ovládací prvek v subsystému WPF

Pomocí Windows Presentation Foundation (WPF) můžete přizpůsobit vzhled existujícího ovládacího prvku vlastním opakovaně použitelným stylem. Styly lze globálně použít pro vaši aplikaci, okna a stránky nebo přímo k ovládacím prvkům.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Vytvoření stylu

Můžete si představit <xref:System.Windows.Style> jako pohodlný způsob, jak použít sadu hodnot vlastností na jeden nebo více prvků. Můžete použít styl na jakémkoli prvku, který je odvozen z <xref:System.Windows.FrameworkElement> nebo jako <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Button> .

Nejběžnější způsob, jak deklarovat styl, je jako prostředek v `Resources` oddílu v souboru XAML. Vzhledem k tomu, že styly jsou prostředky, řídí se stejnými pravidly oboru, která se vztahují na všechny prostředky. Put, kde deklarujete styl, ovlivňuje, kde lze použít styl. Například pokud deklarujete styl v kořenovém elementu souboru XAML definice aplikace, styl lze použít kdekoli v aplikaci.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Pokud deklarujete styl v jednom ze souborů XAML aplikace, styl lze použít pouze v tomto souboru XAML. Další informace o pravidlech oboru pro prostředky naleznete v tématu [prostředky XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Styl se skládá z `<Setter>` podřízených prvků, které nastavují vlastnosti na prvcích, na které se styl aplikuje. V předchozím příkladu si všimněte, že styl je nastaven na hodnotu použít na `TextBlock` typy prostřednictvím `TargetType` atributu. Styl nastaví na <xref:System.Windows.Controls.Control.FontSize%2A> `15` a <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold` . Přidejte `<Setter>` pro každou vlastnost styl, který se změní.

## <a name="apply-a-style-implicitly"></a>Implicitně použít styl

A <xref:System.Windows.Style> je pohodlný způsob, jak použít sadu hodnot vlastností na více než jeden prvek. Zvažte například následující <xref:System.Windows.Controls.TextBlock> prvky a jejich výchozí vzhled v okně.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Ukázka stylu snímku obrazovky](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Výchozí vzhled lze změnit nastavením vlastností, jako jsou například <xref:System.Windows.Controls.Control.FontSize%2A> a <xref:System.Windows.Controls.Control.FontFamily%2A> , u každého <xref:System.Windows.Controls.TextBlock> prvku přímo. Pokud však chcete <xref:System.Windows.Controls.TextBlock> , aby prvky sdílely některé vlastnosti, můžete vytvořit <xref:System.Windows.Style> v `Resources` části souboru XAML, jak je znázorněno zde.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Když nastavíte <xref:System.Windows.Style.TargetType%2A> styl na <xref:System.Windows.Controls.TextBlock> typ a vynecháte `x:Key` atribut, použije se styl pro všechny <xref:System.Windows.Controls.TextBlock> prvky, které jsou vymezeny na styl, což je obecně samotný soubor XAML.

Nyní se <xref:System.Windows.Controls.TextBlock> prvky zobrazí takto.

![Ukázka stylu snímku obrazovky](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Použít styl explicitně

Pokud přidáte `x:Key` atribut s hodnotou do stylu, styl již nebude implicitně aplikován na všechny prvky objektu <xref:System.Windows.Style.TargetType%2A> . Na elementy, které mají explicitně odkaz na styl, se použije styl.

Tady je styl z předchozí části, ale deklarovaný s `x:Key` atributem.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Chcete-li použít styl, nastavte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost prvku na `x:Key` hodnotu pomocí [rozšíření značek StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), jak je znázorněno zde.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Všimněte si, že první <xref:System.Windows.Controls.TextBlock> prvek má použit styl, zatímco druhý element TextBlock zůstane beze změny. Implicitní styl z předchozí části byl změněn na styl, který deklaruje `x:Key` atribut, což znamená, že jediným prvkem ovlivněným stylem je ten, který na styl odkazoval přímo.

![Ukázka stylu snímku obrazovky](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "Vytvoření-a-Style – Explicit – TextBlock")

Když je styl použit, explicitně nebo implicitně, bude uzavřen a nelze jej změnit. Chcete-li změnit styl, který byl použit, vytvořte nový styl, který nahradí stávající. Další informace najdete v tématu <xref:System.Windows.Style.IsSealed%2A> vlastnost.

Můžete vytvořit objekt, který zvolí styl, který se použije v závislosti na vlastní logice. Příklad naleznete v příkladu, který je k dispozici pro <xref:System.Windows.Controls.StyleSelector> třídu.

## <a name="apply-a-style-programmatically"></a>Použití stylu programově

Chcete-li přiřadit pojmenované styly k elementu programově, Získejte styl z kolekce Resources a přiřaďte ji k vlastnosti elementu <xref:System.Windows.FrameworkElement.Style%2A> . Položky v kolekci prostředků jsou typu <xref:System.Object> . Proto je nutné přetypování načteného stylu na typ <xref:System.Windows.Style?displayProperty=fullName> před jeho přiřazením do `Style` Vlastnosti. Například následující kód nastaví styl `TextBlock` pojmenovaného `textblock1` na definovaný styl `TitleText` .

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Roztažení stylu

Možná budete chtít <xref:System.Windows.Controls.TextBlock> , aby vaše dva prvky sdílely některé hodnoty vlastností, například <xref:System.Windows.Controls.Control.FontFamily%2A> a uprostřed <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> . Ale také budete chtít **, aby měl text má** další vlastnosti. To lze provést vytvořením nového stylu, který je založen na prvním stylu, jak je znázorněno zde.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Tento `TextBlock` styl je nyní zarovnán na střed, používá `Comic Sans MS` písmo, které má velikost `26` , a barvu popředí nastavenou na hodnotu <xref:System.Windows.Media.LinearGradientBrush> zobrazenou v příkladu. Všimněte si, že Přepisuje <xref:System.Windows.Controls.Control.FontSize%2A> hodnotu základního stylu. Pokud je k dispozici více než jeden <xref:System.Windows.Setter> ukazatel ukazující na stejnou vlastnost v rámci <xref:System.Windows.Style> , má `Setter` přednost deklarace, která je deklarována jako poslední.

Následující příklad ukazuje, co <xref:System.Windows.Controls.TextBlock> prvky teď vypadají jako:

![TextBlocks ve stylu](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Tento `TitleText` styl rozšiřuje styl, který byl vytvořen pro <xref:System.Windows.Controls.TextBlock> typ, na který odkazuje `BasedOn="{StaticResource {x:Type TextBlock}}"` . Styl, který má, lze také zvětšit `x:Key` pomocí `x:Key` stylu. Pokud se například použil styl s názvem `Header1` a chtěli jste tento styl zvětšit, použijete `BasedOn="{StaticResource Header1}"` .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Vztah vlastnosti TargetType a atributu X:Key –

Jak bylo uvedeno dříve, nastavení <xref:System.Windows.Style.TargetType%2A> vlastnosti na hodnotu `TextBlock` bez přiřazení stylu `x:Key` způsobí, že styl bude použit pro všechny <xref:System.Windows.Controls.TextBlock> elementy. V tomto případě `x:Key` je implicitně nastaven na `{x:Type TextBlock}` . To znamená, že pokud explicitně nastavíte `x:Key` hodnotu na jinou než `{x:Type TextBlock}` , <xref:System.Windows.Style> není použita na všechny `TextBlock` prvky automaticky. Místo toho je nutné použít styl (pomocí `x:Key` hodnoty) na `TextBlock` elementy explicitně. Pokud je váš styl v části Resources (prostředky) a nenastavíte `TargetType` vlastnost na styl, je nutné nastavit `x:Key` atribut.

Kromě poskytování výchozí hodnoty pro `x:Key` , `TargetType` vlastnost určuje typ, pro který se aplikuje vlastnosti setter. Pokud nezadáte, je `TargetType` nutné kvalifikovat vlastnosti <xref:System.Windows.Setter> objektů pomocí názvu třídy pomocí syntaxe `Property="ClassName.Property"` . Například místo nastavení `Property="FontSize"` musíte nastavit <xref:System.Windows.Setter.Property%2A> na `"TextBlock.FontSize"` nebo `"Control.FontSize"` .

Všimněte si také, že mnoho ovládacích prvků WPF sestává z kombinace jiných ovládacích prvků WPF. Vytvoříte-li styl, který se vztahuje na všechny ovládací prvky typu, mohou se zobrazit neočekávané výsledky. Například pokud vytvoříte styl, který cílí na <xref:System.Windows.Controls.TextBlock> typ v <xref:System.Windows.Window> , styl bude použit pro všechny `TextBlock` ovládací prvky v okně, a to i v případě, že `TextBlock` je součástí jiného ovládacího prvku, jako je například <xref:System.Windows.Controls.ListBox> .

## <a name="see-also"></a>Viz také

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Přehled prostředků XAML](xaml-resources-define.md)
- [Přehled XAML (WPF & .NET Core)](xaml.md)
