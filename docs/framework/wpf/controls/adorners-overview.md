---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111176"
---
# <a name="adorners-overview"></a>Přehled doplňků

Adorners jsou speciální <xref:System.Windows.FrameworkElement>typ , který slouží k poskytování vizuální podněty pro uživatele. Mezi další použití Adorners lze přidat funkční popisovače prvků nebo poskytnout informace o stavu ovládacího prvku.

## <a name="about-adorners"></a>O adorners

A <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.FrameworkElement> vlastní, který <xref:System.Windows.UIElement>je vázán na . Adorners jsou vykresleny <xref:System.Windows.Documents.AdornerLayer>v , což je vykreslovací povrch, který je vždy nad objektem adorned element nebo kolekce adorned prvky. Vykreslování adorner <xref:System.Windows.UIElement> je nezávislý na vykreslování adorner je vázán. Adorner je obvykle umístěn vzhledem k prvku, ke kterému je vázán, pomocí standardní 2D souřadnice původu umístěného v levém horním rohu adorned elementu.

Běžné aplikace pro adorners patří:

- Přidání funkčních <xref:System.Windows.UIElement> úchytů, které umožňují uživateli nějakým způsobem manipulovat s prvkem (změna velikosti, otočení, změna umístění atd.).
- Poskytněte vizuální zpětnou vazbu k označení různých stavů nebo v reakci na různé události.
- Překryvné vizuální <xref:System.Windows.UIElement>dekorace na .
- Vizuálně maskovat nebo přepsat část <xref:System.Windows.UIElement>nebo celý .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje základní rámec pro zdobení vizuálních prvků. V následující tabulce jsou uvedeny primární typy používané při ozdobení objektů a jejich účel. Následuje několik příkladů použití:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třídy, ze kterého zdědí všechny konkrétní adorner implementace.|
|<xref:System.Windows.Documents.AdornerLayer>|Třída představující vykreslovací vrstvu pro adorner (y) jednoho nebo více ozdobných prvků.|
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje adorner vrstvy, které mají být spojeny s kolekcí prvků.|

## <a name="implementing-a-custom-adorner"></a>Implementace vlastní adorner

Adorners rámec poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určena především pro podporu vytváření vlastní adorners. Vlastní adorner je vytvořen implementací třídy, <xref:System.Windows.Documents.Adorner> která dědí z abstraktní třídy.

> [!NOTE]
> Nadřazený <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> je, který <xref:System.Windows.Documents.Adorner>vykreslí , není prvek zdobí.

Následující příklad ukazuje třídu, která implementuje jednoduchý adorner. Příklad adorner jednoduše zdobí rohy <xref:System.Windows.UIElement> s kruhy.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Následující obrázek znázorňuje SimpleCircleAdorner aplikovaný na <xref:System.Windows.Controls.TextBox>:

![Snímek obrazovky s ozdobným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Chování vykreslování pro adornery

Je důležité si uvědomit, že adorners neobsahují žádné vlastní vykreslování chování; zajištění, že adorner vykreslí je odpovědnost adorner implementer. Běžným způsobem implementace chování vykreslování je přepsat metodu <xref:System.Windows.UIElement.OnRender%2A> a použít jeden nebo více <xref:System.Windows.Media.DrawingContext> objektů k vykreslení vizuálů adorner podle potřeby (jak je znázorněno v příkladu výše).

> [!NOTE]
> Vše, co je umístěno ve vrstvě adorner, je vykresleno nad ostatními styly, které jste nastavili. Jinými slovy adorners jsou vždy vizuálně na vrcholu a nelze přepsat pomocí pořadí vykreslovat.

## <a name="events-and-hit-testing"></a>Události a testování přístupů

Adorners přijímat vstupní události, <xref:System.Windows.FrameworkElement>stejně jako všechny ostatní .  Vzhledem k tomu, že adorner má vždy vyšší pořadí vykreslování <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove>než prvek, který zdobí, adorner obdrží vstupní události (například nebo ) které mohou být určeny pro základní adorned element.  Adorner můžete naslouchat pro určité vstupní události a předat je na základní adorned prvek re-raising události.

Chcete-li povolit předávací přístupů testování <xref:System.Windows.UIElement.IsHitTestVisible%2A> prvků pod adorner, nastavte vlastnost test přístupů na **false** na adorner.  Další informace o testování přístupů naleznete [v tématu Testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Ozdobit jeden prvek uielement

Chcete-li svázat adorner na konkrétní <xref:System.Windows.UIElement>, postupujte takto:

1. Volání statické <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody získat <xref:System.Windows.Documents.AdornerLayer> objekt <xref:System.Windows.UIElement> pro být adorned. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>prochází vizuální strom, počínaje zadanou <xref:System.Windows.UIElement>a vrátí první adorner vrstvu, kterou najde. (Pokud jsou nalezeny žádné adorner vrstvy, metoda vrátí null.)

2. Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody svázat adorner k <xref:System.Windows.UIElement>cíli .

 Následující příklad váže SimpleCircleAdorner (viz výše) <xref:System.Windows.Controls.TextBox> s názvem *myTextBox*:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] svázat adorner na jiný prvek není aktuálně podporována.

## <a name="adorning-the-children-of-a-panel"></a>Ozdobit děti panelu

Chcete-li svázat adorner <xref:System.Windows.Controls.Panel>s podřízenými objekty , postupujte takto:

1. Volání `static` metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít adorner vrstvu pro prvek, jehož podřízené objekty mají být adorned.

2. Výčet prostřednictvím podřízených nadřazený prvek a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody svázat adorner na každý podřízený prvek.

Následující příklad váže SimpleCircleAdorner (viz výše) na <xref:System.Windows.Controls.StackPanel> podřízené s názvem *myStackPanel*:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Přehled objektů Shape a základního kreslení ve WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled vykreslovaných objektů](../graphics-multimedia/drawing-objects-overview.md)
- [Témata s postupy](adorners-how-to-topics.md)
