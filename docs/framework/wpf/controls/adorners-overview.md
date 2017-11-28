---
title: "Přehled doplňků"
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
helpviewer_keywords: adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42e37a1a1c00ab1a2039eba5f310cadf9a2175c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adorners-overview"></a>Přehled doplňků
Ozdobného prvku se o zvláštní typ <xref:System.Windows.FrameworkElement>používané k poskytování vizuální upozornění uživatele. Mezi další používá ozdobného prvku slouží k přidejte funkční obslužné rutiny na elementy nebo zadejte informace o prvku stavu.  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>O ozdobného prvku  
 <xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement> která je vázaná <xref:System.Windows.UIElement>. Ozdobného prvku se zobrazují v <xref:System.Windows.Documents.AdornerLayer>, což je vykreslování prostor, který je pořád nad ozdobné element nebo kolekci elementů ozdobné. Vykreslování adorner je nezávislé na vykreslování <xref:System.Windows.UIElement> s vazbou adorner na. Adorner je obvykle umístěné vzhledem k elementu, ke kterému je vázán, pomocí standardní počátek souřadnic 2-D umístěný v levé horní ozdobné elementu.  
  
 Běžné aplikace pro ozdobného prvku patří:  
  
-   Přidání funkční obslužné rutiny na <xref:System.Windows.UIElement> které umožňují uživatelům pracovat s element nějakým způsobem (Změna velikosti, otáčení, změna umístění atd.).  
  
-   Vizuální zpětnou vazbu k označení různé stavy, nebo v reakci na různé události.  
  
-   Překrytí visual dekorace na <xref:System.Windows.UIElement>.  
  
-   Vizuální maskování nebo přepsání část nebo všechny <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje základní architekturu pro adorning vizuální prvky. Následující tabulka uvádí primární typy používané při adorning objekty a jejich účel. Postupujte podle několik příkladů použití.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Abstraktní základní třída, ze které dědí všechny adorner konkrétní implementace.|  
|<xref:System.Windows.Documents.AdornerLayer>|Třída představující vrstvu vykreslování pro adorner(s) jeden nebo více ozdobné elementů.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Třída, která umožňuje vrstvu adorner přidruženou kolekci elementů.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementace vlastních Adorner  
 Rozhraní framework ozdobného prvku poskytované [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určená hlavně pro podporu vytváření vlastní ozdobného prvku. Vlastní adorner je vytvořen pomocí implementace třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.  
  
> [!NOTE]
>  Nadřazeného <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer> , vykreslí <xref:System.Windows.Documents.Adorner>, není právě ozdobené elementu.  
  
 Následující příklad ukazuje třídu, která implementuje jednoduché adorner. Příklad adorner jednoduše adorns rozích <xref:System.Windows.UIElement> s kroužky.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Následující obrázek ukazuje SimpleCircleAdorner u <xref:System.Windows.Controls.TextBox>.  
  
 ![Příklad ozdobného prvku: Ozdobné textové pole](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Vykreslování chování ozdobného prvku  
 Je důležité si uvědomit, že ozdobného prvku neobsahují žádné vyplývajících vykreslování chování; zajištění, že adorner vykreslí má na starosti implementátor adorner.   Běžný způsob implementace vykreslování chování je přepsat <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> pro vykreslení adorner vizuály podle potřeby (jak je uvedeno v předchozím příkladu).  
  
> [!NOTE]
>  Nic umístěny ve vrstvě adorner vykreslením nad zbytek všech stylů, které jste nastavili. Jinými slovy ozdobného prvku jsou vždy vizuálně nahoře a nelze ji přepsat pomocí pořadí z-order.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Události a přístupů testování  
 Ozdobného prvku přijímat vstupní události stejně jako libovolný jiný <xref:System.Windows.FrameworkElement>.  Protože adorner vždy má vyšší pořadí vykreslování než element ho adorns, adorner obdrží vstupních událostech (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove>), může být žádoucí pro základní ozdobené elementu.  Adorner může sledovat určité vstupní události a odesílat základní ozdobné element podle znovu vyvolá událost.  
  
 Pokud chcete povolit průchozí přístupů testování elementů v rámci adorner, nastavte přístupů test <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost **false** na adorner.  Další informace o počtu testování najdete v tématu  
  
 [Testování v Visual vrstvě průchodu](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Adorning jeden prvků uživatelského rozhraní  
 K vytvoření vazby adorner konkrétní <xref:System.Windows.UIElement>, postupujte takto:  
  
1.  Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> k být ozdobené. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede až vizuálním stromu, začínající v zadaném <xref:System.Windows.UIElement>a vrátí první vrstvu adorner najde. (Pokud se nenajdou žádné adorner vrstvy, metoda vrátí hodnotu null.)  
  
2.  Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner k cíli <xref:System.Windows.UIElement>.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Adorning podřízených prvků panely  
 Při vytváření vazby adorner podřízených objektů daného <xref:System.Windows.Controls.Panel>, postupujte takto:  
  
1.  Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít vrstvu adorner pro element, jehož podřízené objekty mají být ozdobené.  
  
2.  Zobrazení výčtu prostřednictvím podřízené objekty daného nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner každý podřízený element.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) u podřízených objektů daného <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [Tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
