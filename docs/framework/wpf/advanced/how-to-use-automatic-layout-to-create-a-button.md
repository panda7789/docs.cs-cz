---
title: "Postupy: Vytvoření tlačítka pomocí automatického rozložení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d55dc1330c21e7eb9f7cfd7f554234dccd6f274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Postupy: Vytvoření tlačítka pomocí automatického rozložení
Tento příklad popisuje postup k vytvoření tlačítka v lokalizovatelný aplikaci, použijte postup automatického rozložení.  
  
 Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces. Často překladatelům při lokalizaci potřeba jeho velikost a umístění elementy kromě překlad textu. V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy. Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které se potřeby pro úpravu. Přístup pro zápis aplikace, které může být snadněji změněnou a přemístěných nazývá `automatic layout`.  
  
 Následující dva [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady vytvářet aplikace, které doložit tlačítko; jednu anglické textem a jednu s španělské text. Všimněte si, že kód je stejný, s výjimkou textu. tlačítko upraví podle textu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup ukázky kódu.  
  
 ![Tlačítko stejné s textem v různých jazycích](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Tlačítko automaticky s možností změny velikosti  
  
## <a name="see-also"></a>Viz také  
 [Použít automatické rozložení – přehled](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Pomocí automatického rozložení mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
