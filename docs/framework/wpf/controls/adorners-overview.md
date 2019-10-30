---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 22d9b1eddbb6db47fb15deebf94cfc5f8d37a380
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040835"
---
# <a name="adorners-overview"></a>Přehled doplňků

Doplňky jsou speciálním typem <xref:System.Windows.FrameworkElement>, který slouží k poskytování vizuálních pomůcek uživateli. Mimo jiné použití Doplňky lze použít k přidání funkčních obslužných rutin do prvků nebo k poskytnutí informací o stavu ovládacího prvku.

## <a name="about-adorners"></a>O doplňkových Doplňkůch

<xref:System.Windows.Documents.Adorner> je vlastní <xref:System.Windows.FrameworkElement>, která je vázána na <xref:System.Windows.UIElement>. Doplňky jsou vykresleny v <xref:System.Windows.Documents.AdornerLayer>, což je plocha vykreslování, která je vždy nad přívrchním prvkem nebo kolekcí doplňkových prvků. Vykreslování doplňku je nezávislé na vykreslování <xref:System.Windows.UIElement>, ke kterému je doplněk vázán. Doplněk je obvykle umístěn vzhledem k elementu, ke kterému je svázán, pomocí standardního zdroje souřadnic 2D v levém horním rohu nataženého prvku.

Mezi běžné aplikace pro doplňky patří:

- Přidání funkčních obslužných rutin do <xref:System.Windows.UIElement>, které umožňují uživateli manipulovat s prvkem nějakým způsobem (Změna velikosti, otočení, přemístění atd.).
- Poskytněte vizuální zpětnou vazbu pro indikaci různých stavů nebo v reakci na různé události.
- Překrytí vizuálních dekorace na <xref:System.Windows.UIElement>.
- Vizuálně maskovat nebo přepsat část nebo všechny <xref:System.Windows.UIElement>.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje základní rámec pro doplňky vizuálních prvků. V následující tabulce jsou uvedeny primární typy používané při příchodu objektů a jejich účel. Několik příkladů použití je následující:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třída, ze které všechny konkrétní implementace doplňků dědí.|
|<xref:System.Windows.Documents.AdornerLayer>|Třída, která představuje vrstvu vykreslování pro doplňky jednoho nebo více prvků s přístupnými doplňky.|
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje přidružit vrstvu doplňků ke kolekci elementů.|

## <a name="implementing-a-custom-adorner"></a>Implementace vlastního doplňku

Doplňky, které poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], jsou určené hlavně pro podporu vytváření vlastních doplňků. Vlastní doplňky je vytvořeno implementací třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.

> [!NOTE]
> Nadřazený objekt <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer>, který vykresluje <xref:System.Windows.Documents.Adorner>, nikoli prvku navýšený.

Následující příklad ukazuje třídu, která implementuje jednoduché doplňky. Vzorový doplňky jednoduše navýšení rohů <xref:System.Windows.UIElement> s kroužky.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Na následujícím obrázku vidíte SimpleCircleAdorner, která se aplikuje na <xref:System.Windows.Controls.TextBox>:

![Snímek obrazovky se zobrazeným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Chování vykreslování pro Doplňky

Je důležité si uvědomit, že doplňky neobsahují žádné podstatné chování při vykreslování; zajištění, že se nakreslí doplňková událost, je odpovědností dodatečně implementátor. Běžným způsobem implementace chování vykreslování je přepsání metody <xref:System.Windows.UIElement.OnRender%2A> a použití jednoho nebo více objektů <xref:System.Windows.Media.DrawingContext> k vykreslení vizuálů doplňku podle potřeby (jak je znázorněno v příkladu výše).

> [!NOTE]
> Cokoli, co umístíte do doplňku, se vykreslí nad zbývajícími styly, které jste nastavili. Jinými slovy, doplňky jsou vždy vizuálně nahoře a nelze je přepsat pomocí pořadí vykreslování.

## <a name="events-and-hit-testing"></a>Události a testování přístupů

Doplňky dostávají vstupní události stejně jako jakékoli jiné <xref:System.Windows.FrameworkElement>.  Vzhledem k tomu, že doplněk má vždy vyšší pořadí z, než je prvek, který je tím větší, doplňky obdrží vstupní události (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove>), které mohou být určeny pro základní prvek s příčím.  Doplňková událost může naslouchat určitým vstupním událostem a předávat je základnímu prvku, který ho znovu vyvolal.

Chcete-li povolit testování průchozího průchodu prvků v doplňku, nastavte u doplňku vlastnost <xref:System.Windows.UIElement.IsHitTestVisible%2A> testu na **hodnotu false** .  Další informace o testování přístupů naleznete v tématu [testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Navýšení jednoho prvku UIElement

K navázání doplňku na konkrétní <xref:System.Windows.UIElement>použijte následující postup:

1. Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro získání <xref:System.Windows.Documents.AdornerLayer> objektu pro <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> provede sestavování vizuálního stromu, počínaje zadaným <xref:System.Windows.UIElement>a vrátí první nalezenou vrstvu doplňku. (Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)

2. Voláním metody <xref:System.Windows.Documents.AdornerLayer.Add%2A> navažte doplňku na cílový <xref:System.Windows.UIElement>.

 Následující příklad váže SimpleCircleAdorner (zobrazený výše) na <xref:System.Windows.Controls.TextBox> s názvem *MyTextBox*:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k navázání doplňku na jiný element není aktuálně podporováno.

## <a name="adorning-the-children-of-a-panel"></a>Vylepšení podřízených objektů panelu

Chcete-li navazovat Doplňky na podřízené objekty <xref:System.Windows.Controls.Panel>, postupujte takto:

1. Voláním metody `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Najděte dodatečnou vrstvu pro element, jehož podřízené prvky mají být nakryté.

2. Vytvořte výčet prostřednictvím podřízených objektů nadřazeného prvku a zavolejte metodu <xref:System.Windows.Documents.AdornerLayer.Add%2A> pro svázání doplňku s každým podřízeným elementem.

Následující příklad váže SimpleCircleAdorner (zobrazený výše) na podřízené položky <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Přehled objektů Shape a základního kreslení ve WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled nakreslených objektů](../graphics-multimedia/drawing-objects-overview.md)
- [Témata s postupy](adorners-how-to-topics.md)
