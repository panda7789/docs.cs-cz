---
title: "TextBlock – přehled"
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
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 404f5677bca0df45d4f7dbf689a297499b36bbab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="textblock-overview"></a>TextBlock – přehled
<xref:System.Windows.Controls.TextBlock> Řízení poskytuje flexibilní text podporu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Element je určena především basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, které nevyžadují více než jeden odstavec textu. Podporuje několik vlastností, které umožňují přesnou kontrolou nad prezentací, jako například <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, a <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Obsah textu lze přidat pomocí <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost. Při použití v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], obsah mezi open a ukončovací značka je implicitně přidán jako text elementu.  
  
 A <xref:System.Windows.Controls.TextBlock> element může být vytvořena instance velmi jednoduše pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 Podobně využití <xref:System.Windows.Controls.TextBlock> elementu v kódu je poměrně jednoduché.  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Label>
