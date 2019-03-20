---
title: 'Postupy: Vytvoření tlačítka pomocí automatického rozložení'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 185bf71d4105d10a2bb85e6a0abd9da63c7d26f0
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185451"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Postupy: Vytvoření tlačítka pomocí automatického rozložení
Tento příklad popisuje, jak automatické rozložení metodu použijte, chcete-li vytvořit tlačítko v lokalizovatelných aplikacích.  
  
 Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces. Lokalizátoři často nutné velikost a umístění prvků kromě překlad textu. V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy. Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které tak snížit potřeba úpravy. Přístup k vytváření aplikací, které se dají snadno změněnou velikostí a přemístěných se nazývá `automatic layout`.  
  
## <a name="example"></a>Příklad  

Následující dva [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady vytvářet aplikace pro vytvoření instance tlačítka; jednu se anglický text a jednu s textem španělština. Všimněte si, že kód je stejná s výjimkou textu. Upraví tlačítka podle textu.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup z ukázek kódu.  
  
 ![Stejné tlačítko s textem v různých jazycích](./media/globalizationbutton.png "GlobalizationButton")  
Tlačítko automaticky umožňující změnu velikosti  
  
## <a name="see-also"></a>Viz také:

- [Přehled automatického rozložení](use-automatic-layout-overview.md)
- [Automatické rozložení použitím mřížky](how-to-use-a-grid-for-automatic-layout.md)
