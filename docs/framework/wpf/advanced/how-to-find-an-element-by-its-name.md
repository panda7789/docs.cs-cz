---
title: "Postupy: Hledání elementu podle názvu"
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 62e5cc9c65afe9da9c77d06c103e99d3ff8d995a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a><span data-ttu-id="55a9a-102">Postupy: Hledání elementu podle názvu</span><span class="sxs-lookup"><span data-stu-id="55a9a-102">How to: Find an Element by Its Name</span></span>
<span data-ttu-id="55a9a-103">Tento příklad popisuje postup použití <xref:System.Windows.FrameworkElement.FindName%2A> metody k vyhledání element podle jeho <xref:System.Windows.FrameworkElement.Name%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="55a9a-103">This example describes how to use the <xref:System.Windows.FrameworkElement.FindName%2A> method to find an element by its <xref:System.Windows.FrameworkElement.Name%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a9a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="55a9a-104">Example</span></span>  
 <span data-ttu-id="55a9a-105">V tomto příkladu se jako obslužné rutiny události tlačítka s zapíše metody k vyhledání konkrétní prvek jeho název.</span><span class="sxs-lookup"><span data-stu-id="55a9a-105">In this example, the method to find a particular element by its name is written as the event handler of a button.</span></span> <span data-ttu-id="55a9a-106">`stackPanel`je <xref:System.Windows.FrameworkElement.Name%2A> kořenové <xref:System.Windows.FrameworkElement> prohledávaný, a metodu příklad pak vizuálně označuje nalezen element podle přetypování jej jako <xref:System.Windows.Controls.TextBlock> a změna jednoho z <xref:System.Windows.Controls.TextBlock> viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55a9a-106">`stackPanel` is the <xref:System.Windows.FrameworkElement.Name%2A> of the root <xref:System.Windows.FrameworkElement> being searched, and the example method then visually indicates the found element by casting it as <xref:System.Windows.Controls.TextBlock> and changing one of the <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] properties.</span></span>  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
