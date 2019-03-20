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
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="3f5b5-102">Postupy: Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="3f5b5-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="3f5b5-103">Tento příklad popisuje, jak automatické rozložení metodu použijte, chcete-li vytvořit tlačítko v lokalizovatelných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="3f5b5-104">Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="3f5b5-105">Lokalizátoři často nutné velikost a umístění prvků kromě překlad textu.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="3f5b5-106">V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="3f5b5-107">Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které tak snížit potřeba úpravy.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="3f5b5-108">Přístup k vytváření aplikací, které se dají snadno změněnou velikostí a přemístěných se nazývá `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f5b5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f5b5-109">Example</span></span>  

<span data-ttu-id="3f5b5-110">Následující dva [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady vytvářet aplikace pro vytvoření instance tlačítka; jednu se anglický text a jednu s textem španělština.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-110">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="3f5b5-111">Všimněte si, že kód je stejná s výjimkou textu. Upraví tlačítka podle textu.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-111">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="3f5b5-112">Následující obrázek ukazuje výstup z ukázek kódu.</span><span class="sxs-lookup"><span data-stu-id="3f5b5-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="3f5b5-113">![Stejné tlačítko s textem v různých jazycích](./media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="3f5b5-113">![The same button with text in different languages](./media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="3f5b5-114">Tlačítko automaticky umožňující změnu velikosti</span><span class="sxs-lookup"><span data-stu-id="3f5b5-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5b5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f5b5-115">See also</span></span>

- [<span data-ttu-id="3f5b5-116">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="3f5b5-116">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="3f5b5-117">Automatické rozložení použitím mřížky</span><span class="sxs-lookup"><span data-stu-id="3f5b5-117">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
