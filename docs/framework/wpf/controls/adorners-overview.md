---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: d8e6e53edc92a2847c001377706d313cf97cced5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956099"
---
# <a name="adorners-overview"></a>Přehled doplňků
Doplňky jsou speciálním typem <xref:System.Windows.FrameworkElement>, který slouží k poskytování vizuálních pomůcek uživateli. Mimo jiné použití Doplňky lze použít k přidání funkčních obslužných rutin do prvků nebo k poskytnutí informací o stavu ovládacího prvku.  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>O doplňkových Doplňkůch  
 <xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement>,který je svázán s. <xref:System.Windows.UIElement> Doplňky jsou vykresleny v <xref:System.Windows.Documents.AdornerLayer>, což je plocha vykreslování, která je vždy nad přívrchním prvkem nebo kolekcí doplňkových prvků. Vykreslování doplňku je nezávislé na vykreslování <xref:System.Windows.UIElement> , ke kterému je doplněk vázán. Doplněk je obvykle umístěn vzhledem k elementu, ke kterému je svázán, pomocí standardního zdroje souřadnic 2D v levém horním rohu nataženého prvku.  
  
 Mezi běžné aplikace pro doplňky patří:  
  
- Přidání funkčních popisovačů <xref:System.Windows.UIElement> , které uživateli umožňují manipulovat s prvkem nějakým způsobem (Změna velikosti, otočení, přemístění atd.).  
  
- Poskytněte vizuální zpětnou vazbu pro indikaci různých stavů nebo v reakci na různé události.  
  
- Překrytí vizuálních <xref:System.Windows.UIElement>dekorace na.  
  
- Vizuálně maskovat nebo potlačit část nebo vše <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje základní rámec pro doplňky vizuálních prvků. V následující tabulce jsou uvedeny primární typy používané při příchodu objektů a jejich účel. Následuje několik příkladů použití.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třída, ze které všechny konkrétní implementace doplňků dědí.|  
|<xref:System.Windows.Documents.AdornerLayer>|Třída, která představuje vrstvu vykreslování pro doplňky jednoho nebo více prvků s přístupnými doplňky.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje přidružit vrstvu doplňků ke kolekci elementů.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementace vlastního doplňku  
 Doplňky, které poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , jsou určené hlavně pro podporu vytváření vlastních doplňků. Vlastní doplňky je vytvořeno implementací třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.  
  
> [!NOTE]
> Nadřazený <xref:System.Windows.Documents.Adorner> objekt <xref:System.Windows.Documents.Adorner>je, který vykresluje, nikoli element, který je v něm navýšený. <xref:System.Windows.Documents.AdornerLayer>  
  
 Následující příklad ukazuje třídu, která implementuje jednoduché doplňky. Příkladem může být <xref:System.Windows.UIElement> pouze sevýšení rohů s kroužky.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Na následujícím obrázku vidíte SimpleCircleAdorner použité pro <xref:System.Windows.Controls.TextBox>.  
  
 ![Snímek obrazovky se zobrazeným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Chování vykreslování pro Doplňky  
 Je důležité si uvědomit, že doplňky neobsahují žádné podstatné chování při vykreslování; zajištění, že se nakreslí doplňková událost, je odpovědností dodatečně implementátor.   Běžným způsobem, jak implementovat chování vykreslování, je přepsat <xref:System.Windows.UIElement.OnRender%2A> metodu a použít jeden nebo více <xref:System.Windows.Media.DrawingContext> objektů pro vykreslení vizuálů doplňku podle potřeby (jak je znázorněno v příkladu výše).  
  
> [!NOTE]
> Cokoli, co umístíte do doplňku, se vykreslí nad zbývajícími styly, které jste nastavili. Jinými slovy, doplňky jsou vždy vizuálně nahoře a nelze je přepsat pomocí pořadí vykreslování.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Události a testování přístupů  
 Doplňky dostávají vstupní události stejně jako jiné <xref:System.Windows.FrameworkElement>.  Vzhledem k tomu, že má doplňková událost vždy vyšší pořadí z, než je prvek, který je prvkem, může doplněk přijímat vstupní události <xref:System.Windows.UIElement.Drop> ( <xref:System.Windows.UIElement.MouseMove>například nebo), které mohou být určeny pro základní prvek s právy.  Doplňková událost může naslouchat určitým vstupním událostem a předávat je základnímu prvku, který ho znovu vyvolal.  
  
 Chcete-li povolit testování průchozího průchodu prvků v doplňku, nastavte vlastnost test <xref:System.Windows.UIElement.IsHitTestVisible%2A> přístupů na **hodnotu false** u doplňku.  Další informace o testování přístupů najdete v tématu.  
  
 [Testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Navýšení jednoho prvku UIElement  
 Chcete-li navazovat Doplňky na konkrétní <xref:System.Windows.UIElement>, postupujte takto:  
  
1. Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro <xref:System.Windows.Documents.AdornerLayer> získání objektu, <xref:System.Windows.UIElement> který má být podrobnější. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede sestavování vizuálního stromu, počínaje zadaným <xref:System.Windows.UIElement>a vrátí první nalezenou vrstvu doplňku. (Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)  
  
2. Voláním <xref:System.Windows.UIElement>metody navázání doplňku k cíli. <xref:System.Windows.Documents.AdornerLayer.Add%2A>  
  
 Následující příklad váže SimpleCircleAdorner (zobrazený výše) k <xref:System.Windows.Controls.TextBox> pojmenovanému *MyTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Vylepšení podřízených objektů panelu  
 Chcete-li vytvořit navázání doplňku k <xref:System.Windows.Controls.Panel>podřízeným položkám, postupujte následovně:  
  
1. `static` Zavolejte metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro nalezení doplňkové vrstvy pro element, jehož podřízené prvky mají být navrstveny.  
  
2. Zobrazte výčet prostřednictvím podřízených objektů nadřazeného prvku a zavolejte <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro svázání doplňku s každým podřízeným elementem.  
  
 Následující příklad váže SimpleCircleAdorner (zobrazený výše) na podřízené objekty <xref:System.Windows.Controls.StackPanel> pojmenovaného *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Přehled objektů Shape a základního kreslení ve WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled nakreslených objektů](../graphics-multimedia/drawing-objects-overview.md)
- [Témata s postupy](adorners-how-to-topics.md)
