---
title: "Postupy: Přidání obslužné rutiny události pomocí kódu"
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
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 348136a1feaf6e0a0824cf183a2eeec4e10b77fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a>Postupy: Přidání obslužné rutiny události pomocí kódu
Tento příklad ukazuje postup přidání obslužné rutiny události pro element pomocí kódu.  
  
 Pokud chcete přidat obslužné rutiny události pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] již byla načtena elementu a stránce značek, který obsahuje element, je nutné přidat obslužnou rutinu pomocí kódu. Případně pokud vytváříte nahoru k elementu pro aplikaci zcela použití kódu a není deklarace všech elementů pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete volat konkrétní metody pro přidání obslužné rutiny událostí na strom vytvořený element.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá novou <xref:System.Windows.Controls.Button> na existující stránku původně definovaného v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Soubor modelu code-behind implementuje metodu obslužné rutiny události a potom přidá dané metody jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button>.  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] Příklad používá `+=` operátor přiřadit obslužnou rutinu události. Toto je stejný operátor, který slouží k přiřazení obslužnou rutinu v [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model zpracování událostí. [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]nepodporuje tento operátor jako způsob přidání obslužných rutin událostí. Místo toho vyžaduje jednu z dvě techniky:  
  
-   Použití <xref:System.Windows.UIElement.AddHandler%2A> metoda, společně s `AddressOf` operátor, chcete-li implementace obslužných rutin událostí.  
  
-   Použití `Handles` – klíčové slovo jako součást definice obslužná rutina události. Tento postup není zobrazeny zde; v tématu [Visual Basic a zpracování události WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  Přidání obslužné rutiny událostí v původně Analyzovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky je mnohem jednodušší. V rámci objektu elementu, kde chcete přidat obslužné rutiny události přidejte atribut, který odpovídá názvu událost, která chcete zpracovat. Zadejte hodnotu tohoto atributu jako název metody obslužné rutiny události, který jste zadali v souboru kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. Další informace najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) nebo [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled směrované události](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
