---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: c9ac784223a76d7bf10a888617c0d3d25c916c10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702965"
---
# <a name="adorners-overview"></a>Přehled doplňků
Doplňky pro úpravy jsou zvláštní druh <xref:System.Windows.FrameworkElement>, která slouží k poskytování vizuální upozornění na uživatele. Mimo jiné účely je možné přidat funkční zpracovává na prvky nebo poskytují informace o ovládací prvek stavu doplňků pro úpravy.  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>O doplňcích  
 <xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement> , který je vázán <xref:System.Windows.UIElement>. Doplňky pro úpravy se zobrazují v <xref:System.Windows.Documents.AdornerLayer>, což je vykreslovací plochu, který je pořád nad s element nebo kolekci elementů s. Vykreslování doplňku je nezávislý na vykreslování <xref:System.Windows.UIElement> svázané doplněk pro úpravy. Pro úpravy je obvykle umístěn vzhledem k elementu, ke kterému je vázán, pomocí standardní počátek souřadnic 2D nachází v levém horním rohu elementu s.  
  
 Běžné aplikace pro doplňky pro úpravy patří:  
  
-   Přidání funkčnosti popisovače <xref:System.Windows.UIElement> , který umožní uživateli manipulovat s elementu nějakým způsobem (Změna velikosti, otáčení, změna umístění atd.).  
  
-   Vizuální zpětnou vazbu k označení různých státech nebo v reakci na různé události.  
  
-   Překryv visual dekorace na <xref:System.Windows.UIElement>.  
  
-   Vizuálně maskování nebo přepsat některá nebo všechna <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje základní rozhraní pro adorning vizuální prvky. Následující tabulka uvádí hlavní typy používané při adorning objekty a jejich účel. Postupujte podle několik příkladů použití.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třída, ze kterého dědí všechny implementace konkrétní doplněk pro úpravy.|  
|<xref:System.Windows.Documents.AdornerLayer>|Třída představující vrstvu vykreslování pro adorner(s) jeden nebo více elementů s.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje vrstvu doplněk pro úpravy, který se má přidružit kolekci elementů.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementace vlastního doplněk pro úpravy  
 Doplňky pro úpravy framework poskytované [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určený primárně pro vytváření vlastní doplňky pro úpravy. Vlastní doplněk pro úpravy je vytvořen pomocí implementace, která dědí z abstraktní třídy <xref:System.Windows.Documents.Adorner> třídy.  
  
> [!NOTE]
>  Nadřazený prvek <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer> , který vykreslí <xref:System.Windows.Documents.Adorner>, není element se opatřený.  
  
 Následující příklad ukazuje třídu, která implementuje jednoduchou doplněk pro úpravy. Doplněk pro úpravy příklad jednoduše adorns rohů <xref:System.Windows.UIElement> s kruzích.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Následující obrázek ukazuje SimpleCircleAdorner u <xref:System.Windows.Controls.TextBox>.  
  
 ![Příklad doplňků pro úpravy: S textového pole](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Chování vykreslování pro doplňky pro úpravy  
 Je důležité si uvědomit, že doplňky pro úpravy neobsahují žádné vlastní vykreslování chování; zajištění, že pro úpravy vykreslí zodpovídá za implementátora doplněk pro úpravy.   Běžný způsob implementace chování vykreslování je k přepsání <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> objekty k vykreslení doplněk pro úpravy vizuály podle potřeby (jak je znázorněno v příkladu výše).  
  
> [!NOTE]
>  Cokoli, co je umístěn ve vrstvě doplněk pro úpravy je vykreslen na zbytek všechny styly, které jste nastavili. Jinými slovy doplňky pro úpravy jsou vždy vizuálně nahoře a nedají se přepsat použití pořadí vykreslování.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Události a volání testování  
 Doplňky pro úpravy přijímat události vstupu stejně jako jakýkoli jiný <xref:System.Windows.FrameworkElement>.  Protože doplňku má vždy vyšší pořadí vykreslování než element ho adorns, doplněk pro úpravy přijímá vstupní události (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove>), který může být určené pro základní opatřený element.  Pro úpravy můžete očekávat určité vstupní události a předat tyto k elementu s základní opětovné vyvolání události.  
  
 Pokud chcete povolit předávací přístupů testování prvků pro úpravy, nastavte průchodů testů <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost **false** na doplněk pro úpravy.  Další informace o přístupů testování najdete v tématu  
  
 [Ověřování pozice ve vizuální vrstvě](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Adorning jednoho elementu UIElement  
 K připojení doplňku k konkrétní <xref:System.Windows.UIElement>, postupujte podle těchto kroků:  
  
1.  Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> zobrazíte <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> chcete být opatřený. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> provede se vizuální strom začínající v zadaném <xref:System.Windows.UIElement>a vrátí první vrstvu doplněk pro úpravy, které nalezne. (Pokud se nenajdou žádné vrstvy doplněk pro úpravy, metoda vrátí hodnotu null.)  
  
2.  Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro vytvoření vazby doplněk pro úpravy k cíli <xref:System.Windows.UIElement>.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vazbu na jiný prvek pro úpravy v tuto chvíli nepodporuje.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Adorning podřízených položek panelu  
 K připojení doplňku k podřízených položek <xref:System.Windows.Controls.Panel>, postupujte podle těchto kroků:  
  
1.  Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít vrstvu doplněk pro úpravy pro element, jehož potomci mají být opatřený.  
  
2.  Zobrazit výčet prostřednictvím podřízené objekty nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu připojení doplňku k každý podřízený prvek.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) do podřízených položek <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.AdornerHitTestResult>
- [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
