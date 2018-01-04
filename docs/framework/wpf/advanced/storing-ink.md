---
title: "Uložení inkoustu"
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
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ab04db2faafc47349d3b8d21098e9eb931cf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="storing-ink"></a><span data-ttu-id="58021-102">Uložení inkoustu</span><span class="sxs-lookup"><span data-stu-id="58021-102">Storing Ink</span></span>
<span data-ttu-id="58021-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody poskytují podporu pro ukládání rukopisu jako Serialized rukopisu serializovat formátu (Format).</span><span class="sxs-lookup"><span data-stu-id="58021-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="58021-104">Konstruktory pro <xref:System.Windows.Ink.StrokeCollection> třída poskytuje podporu pro čtení dat rukopisu.</span><span class="sxs-lookup"><span data-stu-id="58021-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="58021-105">Element Ink ukládání a načítání</span><span class="sxs-lookup"><span data-stu-id="58021-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="58021-106">Tato část popisuje, jak k ukládání a načítání rukopisu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.</span><span class="sxs-lookup"><span data-stu-id="58021-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="58021-107">Následující příklad implementuje obslužnou rutinu události kliknutí na tlačítko, která představuje uživatele se dialogové okno uložení souboru a uloží očistí od <xref:System.Windows.Controls.InkCanvas> na více systémů do souboru.</span><span class="sxs-lookup"><span data-stu-id="58021-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="58021-108">Následující příklad implementuje obslužnou rutinu události kliknutí na tlačítko, která představuje uživatele se dialogové okno otevřít soubor a přečte rukopisu ze souboru do <xref:System.Windows.Controls.InkCanvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="58021-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="58021-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="58021-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="58021-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="58021-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
