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
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460439"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Postupy: Přidání obslužné rutiny události pomocí kódu
Tento příklad ukazuje, jak přidat obslužnou rutinu události do prvku pomocí kódu.  
  
 Pokud chcete přidat obslužnou rutinu události do prvku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a stránka značek, která obsahuje element, již byla načtena, je nutné přidat obslužnou rutinu pomocí kódu. Případně, pokud vytváříte strom elementů pro aplikaci výhradně pomocí kódu a nedeklarujete žádné prvky pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete volat konkrétní metody pro přidání obslužných rutin událostí do vytvořeného stromu elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá novou <xref:System.Windows.Controls.Button> na existující stránku, která je zpočátku definovaná v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Soubor kódu na pozadí implementuje metodu obslužné rutiny události a následně přidá tuto metodu jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button>.  
  
 V C# příkladu se používá operátor `+=` k přiřazení obslužné rutiny události. Toto je stejný operátor, který se používá k přiřazení obslužné rutiny v modelu zpracování událostí modulu CLR (Common Language Runtime). Microsoft Visual Basic nepodporuje tento operátor jako způsob přidávání obslužných rutin událostí. Místo toho vyžaduje jednu ze dvou postupů:  
  
- Použijte metodu <xref:System.Windows.UIElement.AddHandler%2A> spolu s operátorem `AddressOf`, chcete-li odkazovat na implementaci obslužné rutiny události.  
  
- Použijte klíčové slovo `Handles` jako součást definice obslužné rutiny události. Tato technika se tady nezobrazuje. viz [Visual Basic a zpracování událostí WPF](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> Přidání obslužné rutiny události na původně analyzovanou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku je mnohem jednodušší. V rámci elementu Object, kam chcete přidat obslužnou rutinu události, přidejte atribut, který odpovídá názvu události, kterou chcete zpracovat. Pak zadejte hodnotu tohoto atributu jako název metody obslužné rutiny události, kterou jste definovali v souboru kódu na pozadí stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Další informace naleznete v tématu Přehled [XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) nebo [směrované události](routed-events-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Témata s postupy](events-how-to-topics.md)
