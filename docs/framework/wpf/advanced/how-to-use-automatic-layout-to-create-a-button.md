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
ms.workload: dotnet
ms.openlocfilehash: c642e6491722e9bfe35337d066e3870f5a70f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="f3bdf-102">Postupy: Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="f3bdf-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="f3bdf-103">Tento příklad popisuje postup k vytvoření tlačítka v lokalizovatelný aplikaci, použijte postup automatického rozložení.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="f3bdf-104">Lokalizace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] může být časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="f3bdf-105">Často překladatelům při lokalizaci potřeba jeho velikost a umístění elementy kromě překlad textu.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="f3bdf-106">V minulosti každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla upravena pro požadované úpravy.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="f3bdf-107">Nyní s funkcemi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete navrhnout prvky, které se potřeby pro úpravu.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="f3bdf-108">Přístup pro zápis aplikace, které může být snadněji změněnou a přemístěných nazývá `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="f3bdf-109">Následující dva [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady vytvářet aplikace, které doložit tlačítko; jednu anglické textem a jednu s španělské text.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="f3bdf-110">Všimněte si, že kód je stejný, s výjimkou textu. tlačítko upraví podle textu.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3bdf-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3bdf-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="f3bdf-112">Následující obrázek ukazuje výstup ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="f3bdf-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="f3bdf-113">![Tlačítko stejné s textem v různých jazycích](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="f3bdf-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="f3bdf-114">Tlačítko automaticky s možností změny velikosti</span><span class="sxs-lookup"><span data-stu-id="f3bdf-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bdf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3bdf-115">See Also</span></span>  
 [<span data-ttu-id="f3bdf-116">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="f3bdf-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="f3bdf-117">Automatické rozložení použitím mřížky</span><span class="sxs-lookup"><span data-stu-id="f3bdf-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
