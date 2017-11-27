---
title: "Procházení textu s použitím automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5b3d08c0a6293b6621d9b6debfa4d63c8abaf3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="traverse-text-using-ui-automation"></a>Procházení textu s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] procházení textový obsah dokumentu podle <xref:System.Windows.Automation.Text.TextUnit> přírůstcích.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak procházet obsah textu zprostředkovatele automatizace uživatelského rozhraní. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Metoda přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body <xref:System.Windows.Automation.Text.TextPatternRange>. Tento text rozsah je obvykle degenerovanou rozsah představující bod pro vložení textu.  
  
> [!NOTE]
>  Od jen založený na textu vložené objekty jsou považovány za součást text datového proudu, vložené objekty, například bitové kopie neovlivní `Move` nebo hodnoty.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Každá metoda používající <xref:System.Windows.Automation.Text.TextUnit> bude odložení na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované v případě danou <xref:System.Windows.Automation.Text.TextUnit> nepodporuje ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
