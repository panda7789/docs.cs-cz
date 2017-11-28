---
title: "Postupy: Automatické rozložení pomocí mřížky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d18563c44381a276d15996dff3f9552c46833b4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Postupy: Automatické rozložení pomocí mřížky
Tento příklad popisuje postupy pro použití v metodě automatického rozložení pro vytvoření lokalizovatelný aplikace tabulky.  
  
 Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces. Často překladatelům při lokalizaci muset znovu velikost a změnit umístění elementy kromě překlad textu. V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy. Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které se potřeby pro úpravu. Přístup pro zápis aplikace, které může být snadněji změně velikosti a přemístěných nazývá `auto layout`.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje použití tabulky na pozici některé tlačítka a text. Všimněte si, že výška a šířka buněk jsou nastaveny na `Auto`; proto buňku, která obsahuje tlačítko s bitovou kopií upraví podle bitovou kopii. Protože <xref:System.Windows.Controls.Grid> element můžete upravit na jeho obsah může být užitečné, když se vezme automatického rozložení přístup k navrhování aplikací, které je možné lokalizovat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat mřížka.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup ukázka kódu.  
  
 ![Příklad mřížky](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Mřížka  
  
## <a name="see-also"></a>Viz také  
 [Použít automatické rozložení – přehled](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Použití automatického rozložení pro vytvoření tlačítka](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
