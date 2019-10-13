---
title: Přehled automatického rozložení
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291267"
---
# <a name="use-automatic-layout-overview"></a>Přehled automatického rozložení

Toto téma obsahuje pokyny pro vývojáře, jak psát aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pomocí lokalizovatelných uživatelských rozhraní (uživatelská rozhraní). V minulosti byla lokalizace uživatelského rozhraní časově náročná. Každý jazyk, pro který bylo uživatelské rozhraní upraveno, aby vyžadovalo úpravu pixelu podle pixelu. V dnešní době se správnou návrhovou a pravou normou pro kódování lze uživatelská rozhraní vytvořit tak, aby mohly lokalizovat méně měnit velikost a umístění. Přístup k psaní aplikací, jejichž velikost se dá snadněji měnit a kde se přemístí, se nazývá automatické rozložení a dá se dosáhnout pomocí @no__tho návrhu aplikací-0.

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Výhody použití automatického rozložení

Vzhledem k tomu, že je prezentační systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonný a flexibilní, nabízí možnost rozložení prvků v aplikaci, která se dá upravit tak, aby vyhovovala požadavkům různých jazyků. Následující seznam ukazuje některé výhody automatického rozložení.

- Uživatelské rozhraní se dobře zobrazuje v jakémkoli jazyce.

- Omezuje nutnost znovu nastavit polohu a velikost ovládacích prvků po převodu textu.

- Zmenší nutnost přizpůsobení velikosti okna.

- Rozložení uživatelského rozhraní se v jakémkoli jazyce vykresluje správně.

- Lokalizace může být zmenšena na bod, který je menší než překlad řetězce.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Automatické rozložení a ovládací prvky

Automatické rozložení umožňuje aplikaci automaticky upravit velikost ovládacího prvku. Například ovládací prvek může být změněn tak, aby odpovídal délce řetězce. Tato možnost umožňuje, aby lokalizovat mohli řetězec přeložit; již nepotřebují měnit velikost ovládacího prvku tak, aby odpovídal přeloženému textu. Následující příklad vytvoří tlačítko s anglickým obsahem.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

V tomto příkladu stačí, když uděláte tlačítko pro španělštinu, aby se změnil text. Například

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

Následující obrázek ukazuje výstup ukázek kódu:

![Stejné tlačítko s textem v různých jazycích](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Automatické rozložení a standardy kódování

Použití přístupu automatickým rozložením vyžaduje sadu standardů kódování a návrhu a pravidla pro vytváření plně lokalizovatelnýho uživatelského rozhraní. Následující pokyny vám pomohou při kódování vašeho automatického rozložení.

**Nepoužívat absolutní umístění**

- Nepoužívejte <xref:System.Windows.Controls.Canvas>, protože umisťuje prvky absolutně.

- Ovládací prvky umístěte pomocí <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Grid>.

Diskuzi o různých typech panelů najdete v tématu [Přehled panelů](../controls/panels-overview.md).

**Nenastavit pevnou velikost okna**

- Použijte <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Příklad:

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Přidejte <xref:System.Windows.FrameworkElement.FlowDirection%2A> do kořenového prvku vaší aplikace.

  WPF nabízí pohodlný způsob, jak podporovat vodorovná, obousměrná a vertikální rozložení. V prezentačním rozhraní lze pomocí vlastnosti <xref:System.Windows.FrameworkElement.FlowDirection%2A> definovat rozložení. Vzory směrového směru jsou:

  - @no__t – 0 (LrTb) – horizontální rozložení pro latinku, východní Asii a tak dále.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – obousměrný pro arabštinu, hebrejštinu a tak dále.

**Místo fyzických písem použít složená písma**

- U složených písem není nutné lokalizovat vlastnost <xref:System.Windows.Controls.Control.FontFamily%2A>.

- Vývojáři mohou použít jedno z následujících písem nebo vytvořit vlastní.

  - Globální uživatelské rozhraní
  - Globální síť San Serif
  - Globální Serif

**Přidat XML: lang**

- Přidejte atribut `xml:lang` do kořenového elementu uživatelského rozhraní, jako je například `xml:lang="en-US"` pro anglickou aplikaci.

- Vzhledem k tomu, že složená písma používají `xml:lang` k určení používaného písma, nastavte tuto vlastnost na podporu vícejazyčných scénářů.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Automatické rozložení a mřížky

Element <xref:System.Windows.Controls.Grid> je vhodný pro automatické rozložení, protože umožňuje vývojářům umístit prvky. Ovládací prvek <xref:System.Windows.Controls.Grid> je schopný distribuovat dostupný prostor mezi jeho podřízené prvky pomocí uspořádání sloupců a řádků. Prvky uživatelského rozhraní mohou zahrnovat více buněk a je možné mít mřížky v rámci gridů. Mřížky jsou užitečné, protože umožňují vytvořit a umístit komplexní uživatelské rozhraní. Následující příklad ukazuje použití mřížky k umístění některých tlačítek a textu. Všimněte si, že výška a šířka buněk jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; Proto buňka, která obsahuje tlačítko s obrázkem, se upraví tak, aby odpovídala obrázku.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

Následující obrázek znázorňuje mřížku vytvořenou předchozím kódem.

Mřížka – ![příklad](./media/glob-grid.png "glob_grid") mřížky

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatické rozložení a mřížky pomocí vlastnosti IsSharedSizeScope

Element <xref:System.Windows.Controls.Grid> je užitečný v lokalizovatelných aplikacích pro vytváření ovládacích prvků, které se přizpůsobí obsahu. Občas ale chcete, aby ovládací prvky zachovaly určitou velikost bez ohledu na obsah. Například pokud máte tlačítka "OK", "Storno" a "Procházet", pravděpodobně nechcete, aby se tlačítka vešla do velikosti obsahu. V tomto případě je <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> připojená vlastnost užitečná pro sdílení stejné velikosti mezi více prvky mřížky. Následující příklad ukazuje, jak sdílet data o velikosti sloupců a řádků mezi více prvky <xref:System.Windows.Controls.Grid>.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Úplnou ukázku kódu naleznete v tématu [sdílení vlastností velikosti mezi mřížkami](../controls/how-to-share-sizing-properties-between-grids.md).

## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Vytvoření tlačítka pomocí automatického rozložení](how-to-use-automatic-layout-to-create-a-button.md)
- [Automatické rozložení použitím mřížky](how-to-use-a-grid-for-automatic-layout.md)
