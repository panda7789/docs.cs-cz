---
title: Uložení inkoustu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: d3d33be5e8b5cf9dd7e32a52dfc258aa934c5c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546094"
---
# <a name="storing-ink"></a>Uložení inkoustu
<xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody poskytují podporu pro ukládání rukopisu jako Serialized rukopisu serializovat formátu (Format). Konstruktory pro <xref:System.Windows.Ink.StrokeCollection> třída poskytuje podporu pro čtení dat rukopisu.  
  
## <a name="ink-storage-and-retrieval"></a>Element Ink ukládání a načítání  
 Tato část popisuje, jak k ukládání a načítání rukopisu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.  
  
 Následující příklad implementuje obslužnou rutinu události kliknutí na tlačítko, která představuje uživatele se dialogové okno uložení souboru a uloží očistí od <xref:System.Windows.Controls.InkCanvas> na více systémů do souboru.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Následující příklad implementuje obslužnou rutinu události kliknutí na tlačítko, která představuje uživatele se dialogové okno otevřít soubor a přečte rukopisu ze souboru do <xref:System.Windows.Controls.InkCanvas> elementu.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)
