---
title: 'Postupy: Automatické rozložení pomocí mřížky'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 590ad7292fea572b20ccaa09ce2886724e004a6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227115"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="a4504-102">Postupy: Automatické rozložení pomocí mřížky</span><span class="sxs-lookup"><span data-stu-id="a4504-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="a4504-103">Tento příklad popisuje, jak pomocí mřížky automatické rozložení přístupu k vytvoření lokalizovatelné aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4504-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="a4504-104">Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="a4504-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="a4504-105">Lokalizátoři často potřeba změnit velikost a umístění prvků kromě překlad textu.</span><span class="sxs-lookup"><span data-stu-id="a4504-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="a4504-106">V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy.</span><span class="sxs-lookup"><span data-stu-id="a4504-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="a4504-107">Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které tak snížit potřeba úpravy.</span><span class="sxs-lookup"><span data-stu-id="a4504-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="a4504-108">Přístup k vytváření aplikací, které se dají snadno změně velikosti a přemístěných se nazývá `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="a4504-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="a4504-109">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje použití tabulky na pozici některá tlačítka a text.</span><span class="sxs-lookup"><span data-stu-id="a4504-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="a4504-110">Všimněte si, že výšku a šířku buňky jsou nastaveny na `Auto`; proto nastaví na buňku, která obsahuje tlačítko s imagí podle obrázku.</span><span class="sxs-lookup"><span data-stu-id="a4504-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="a4504-111">Vzhledem k tomu, <xref:System.Windows.Controls.Grid> element můžete upravit na jeho obsah, může být užitečné, když se vezme automatické rozložení přístup k návrhu aplikací, které může být lokalizována.</span><span class="sxs-lookup"><span data-stu-id="a4504-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4504-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4504-112">Example</span></span>  
 <span data-ttu-id="a4504-113">Následující příklad ukazuje, jak pomocí mřížky.</span><span class="sxs-lookup"><span data-stu-id="a4504-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a4504-114">Následující obrázek znázorňuje výstup tohoto ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="a4504-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="a4504-115">![Grid – příklad](./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="a4504-115">![Grid example](./media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="a4504-116">Mřížka</span><span class="sxs-lookup"><span data-stu-id="a4504-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4504-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4504-117">See also</span></span>

- [<span data-ttu-id="a4504-118">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="a4504-118">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="a4504-119">Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="a4504-119">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
