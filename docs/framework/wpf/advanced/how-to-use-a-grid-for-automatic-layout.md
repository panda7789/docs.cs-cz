---
title: 'Postupy: Automatické rozložení pomocí mřížky'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 6ea0b64af07924867c2de97baf5a81f8e8da6a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544619"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="ebcce-102">Postupy: Automatické rozložení pomocí mřížky</span><span class="sxs-lookup"><span data-stu-id="ebcce-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="ebcce-103">Tento příklad popisuje postupy pro použití v metodě automatického rozložení pro vytvoření lokalizovatelný aplikace tabulky.</span><span class="sxs-lookup"><span data-stu-id="ebcce-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="ebcce-104">Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="ebcce-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="ebcce-105">Často překladatelům při lokalizaci muset znovu velikost a změnit umístění elementy kromě překlad textu.</span><span class="sxs-lookup"><span data-stu-id="ebcce-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="ebcce-106">V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy.</span><span class="sxs-lookup"><span data-stu-id="ebcce-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="ebcce-107">Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které se potřeby pro úpravu.</span><span class="sxs-lookup"><span data-stu-id="ebcce-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="ebcce-108">Přístup pro zápis aplikace, které může být snadněji změně velikosti a přemístěných nazývá `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="ebcce-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="ebcce-109">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje použití tabulky na pozici některé tlačítka a text.</span><span class="sxs-lookup"><span data-stu-id="ebcce-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="ebcce-110">Všimněte si, že výška a šířka buněk jsou nastaveny na `Auto`; proto buňku, která obsahuje tlačítko s bitovou kopií upraví podle bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="ebcce-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="ebcce-111">Protože <xref:System.Windows.Controls.Grid> element můžete upravit na jeho obsah může být užitečné, když se vezme automatického rozložení přístup k navrhování aplikací, které je možné lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="ebcce-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebcce-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebcce-112">Example</span></span>  
 <span data-ttu-id="ebcce-113">Následující příklad ukazuje, jak používat mřížka.</span><span class="sxs-lookup"><span data-stu-id="ebcce-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="ebcce-114">Následující obrázek ukazuje výstup ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="ebcce-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="ebcce-115">![Příklad mřížky](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="ebcce-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="ebcce-116">Mřížka</span><span class="sxs-lookup"><span data-stu-id="ebcce-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcce-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebcce-117">See Also</span></span>  
 [<span data-ttu-id="ebcce-118">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="ebcce-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="ebcce-119">Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="ebcce-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
