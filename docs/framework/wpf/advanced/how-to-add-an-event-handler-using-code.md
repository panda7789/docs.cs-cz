---
title: 'Postupy: Přidání obslužné rutiny události pomocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 10f8e0899e61d5d54589c910bdcbcd92d8ee947c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129353"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Postupy: Přidání obslužné rutiny události pomocí kódu
Tento příklad ukazuje, jak přidat obslužnou rutinu události k prvku pomocí kódu.  
  
 Pokud chcete přidat obslužnou rutinu události pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu a na stránce značek, obsahující prvek již byl načten, je nutné přidat obslužnou rutinu pomocí kódu. Případně pokud vytváříte nahoru stromem prvků pro aplikaci zcela pomocí kódu a nedeklarováním všechny prvky pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete volat konkrétní metody pro přidání obslužné rutiny událostí do stromu vytvořený element.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá nový <xref:System.Windows.Controls.Button> na existující stránku, který je původně definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Soubor kódu na pozadí implementuje metodu obslužné rutiny události a pak přidá tuto metodu jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button>.  
  
 C# Příklad používá `+=` operátor přiřazení obslužnou rutinu události. To je stejný operátor, který slouží k přiřazení obslužnou rutinu v [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model zpracování událostí. Microsoft Visual Basic nepodporuje tento operátor jako způsob přidání obslužných rutin událostí. Místo toho vyžaduje jednu z dvou technik:  
  
-   Použití <xref:System.Windows.UIElement.AddHandler%2A> metody společně s `AddressOf` operátor tak, aby odkazovaly implementaci obslužné rutiny události.  
  
-   Použití `Handles` – klíčové slovo jako součást definice obslužné rutiny události. Tato technika, tady není ukázaný; Zobrazit [jazyka Visual Basic a WPF zpracování událostí](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  Přidání obslužné rutiny událostí v původně analyzovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka je mnohem jednodušší. V rámci elementu objektu, ve které chcete přidat obslužnou rutinu události přidejte atribut, který odpovídá názvu události, ke které chcete zpracovat. Hodnota tohoto atributu zadejte jako název obslužné metody událostí, který jste definovali v souboru kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. Další informace najdete v tématu [přehled XAML (WPF)](xaml-overview-wpf.md) nebo [směrovat Přehled událostí](routed-events-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [– postupy](events-how-to-topics.md)
