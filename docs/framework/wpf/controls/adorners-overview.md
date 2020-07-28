---
title: Přehled doplňků
description: Přečtěte si o Windows Presentation Foundation doplňky, speciální typ prvku FrameworkElement, který poskytuje pomůcky pro uživatele, jako jsou funkční popisovače pro prvky.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167735"
---
# <a name="adorners-overview"></a>Přehled doplňků

Doplňky jsou speciálním typem <xref:System.Windows.FrameworkElement> , který slouží k poskytování vizuálních pomůcek uživateli. Mimo jiné použití Doplňky lze použít k přidání funkčních obslužných rutin do prvků nebo k poskytnutí informací o stavu ovládacího prvku.

## <a name="about-adorners"></a>O doplňkových Doplňkůch

<xref:System.Windows.Documents.Adorner>Je vlastní <xref:System.Windows.FrameworkElement> , který je svázán s <xref:System.Windows.UIElement> . Doplňky jsou vykresleny v <xref:System.Windows.Documents.AdornerLayer> , což je plocha vykreslování, která je vždy nad přívrchním prvkem nebo kolekcí doplňkových prvků. Vykreslování doplňku je nezávislé na vykreslování <xref:System.Windows.UIElement> , ke kterému je doplněk vázán. Doplněk je obvykle umístěn vzhledem k prvku, ke kterému je svázán, pomocí standardní 2D souřadnicového zdroje umístěný vlevo nahoře v pravém prvku.

Mezi běžné aplikace pro doplňky patří:

- Přidání funkčních popisovačů <xref:System.Windows.UIElement> , které uživateli umožňují manipulovat s prvkem nějakým způsobem (Změna velikosti, otočení, přemístění atd.).
- Poskytněte vizuální zpětnou vazbu pro indikaci různých stavů nebo v reakci na různé události.
- Překrytí vizuálních dekorace na <xref:System.Windows.UIElement> .
- Vizuálně maskovat nebo potlačit část nebo vše <xref:System.Windows.UIElement> .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje základní rámec pro doplňky vizuálních prvků. V následující tabulce jsou uvedeny primární typy používané při příchodu objektů a jejich účel. Několik příkladů použití je následující:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třída, ze které všechny konkrétní implementace doplňků dědí.|
|<xref:System.Windows.Documents.AdornerLayer>|Třída, která představuje vrstvu vykreslování pro doplňky jednoho nebo více prvků s přístupnými doplňky.|
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje přidružit vrstvu doplňků ke kolekci elementů.|

## <a name="implementing-a-custom-adorner"></a>Implementace vlastního doplňku

Doplňky, které poskytuje, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jsou určené hlavně pro podporu vytváření vlastních doplňků. Vlastní doplňky je vytvořeno implementací třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.

> [!NOTE]
> Nadřazený objekt <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer> , který vykresluje <xref:System.Windows.Documents.Adorner> , nikoli element, který je v něm navýšený.

Následující příklad ukazuje třídu, která implementuje jednoduché doplňky. Příkladem může být pouze sevýšení rohů <xref:System.Windows.UIElement> s kroužky.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Následující obrázek ukazuje SimpleCircleAdorner použitou pro <xref:System.Windows.Controls.TextBox> :

![Snímek obrazovky se zobrazeným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Chování vykreslování pro Doplňky

Je důležité si uvědomit, že doplňky neobsahují žádné podstatné chování při vykreslování; zajištění, že se nakreslí doplňková událost, je odpovědností dodatečně implementátor. Běžným způsobem, jak implementovat chování vykreslování, je přepsat <xref:System.Windows.UIElement.OnRender%2A> metodu a použít jeden nebo více <xref:System.Windows.Media.DrawingContext> objektů pro vykreslení vizuálů doplňku podle potřeby (jak je znázorněno v příkladu výše).

> [!NOTE]
> Cokoli, co umístíte do doplňku, se vykreslí nad zbývajícími styly, které jste nastavili. Jinými slovy, doplňky jsou vždy vizuálně nahoře a nelze je přepsat pomocí pořadí vykreslování.

## <a name="events-and-hit-testing"></a>Události a testování přístupů

Doplňky dostávají vstupní události stejně jako jiné <xref:System.Windows.FrameworkElement> .  Vzhledem k tomu, že má doplňková událost vždy vyšší pořadí z, než je prvek, který je prvkem, může doplněk přijímat vstupní události (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove> ), které mohou být určeny pro základní prvek s právy.  Doplňková událost může naslouchat určitým vstupním událostem a předávat je základnímu prvku, který ho znovu vyvolal.

Chcete-li povolit testování průchozího průchodu prvků v doplňku, nastavte vlastnost test přístupů <xref:System.Windows.UIElement.IsHitTestVisible%2A> na **hodnotu false** u doplňku.  Další informace o testování přístupů naleznete v tématu [testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Navýšení jednoho prvku UIElement

Chcete-li navazovat Doplňky na konkrétní <xref:System.Windows.UIElement> , postupujte takto:

1. Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro získání <xref:System.Windows.Documents.AdornerLayer> objektu, který má být podrobnější <xref:System.Windows.UIElement> . <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede sestavování vizuálního stromu, počínaje zadaným <xref:System.Windows.UIElement> a vrátí první nalezenou vrstvu doplňku. (Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)

2. Voláním <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody navázání doplňku k cíli <xref:System.Windows.UIElement> .

 Následující příklad váže SimpleCircleAdorner (zobrazený výše) k <xref:System.Windows.Controls.TextBox> pojmenovanému *MyTextBox*:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.

## <a name="adorning-the-children-of-a-panel"></a>Vylepšení podřízených objektů panelu

Chcete-li vytvořit navázání doplňku k podřízeným položkám <xref:System.Windows.Controls.Panel> , postupujte následovně:

1. Zavolejte `static` metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro nalezení doplňkové vrstvy pro element, jehož podřízené prvky mají být navrstveny.

2. Zobrazte výčet prostřednictvím podřízených objektů nadřazeného prvku a zavolejte <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro svázání doplňku s každým podřízeným elementem.

Následující příklad váže SimpleCircleAdorner (zobrazený výše) k podřízeným položkám <xref:System.Windows.Controls.StackPanel> pojmenovaného *myStackPanel*:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Tvary a základní kresby v přehledu WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled vykreslovaných objektů](../graphics-multimedia/drawing-objects-overview.md)
- [– postupy](adorners-how-to-topics.md)
