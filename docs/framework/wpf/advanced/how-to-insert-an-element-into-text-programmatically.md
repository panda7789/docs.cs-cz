---
title: "Postupy: Vkládání elementů do textu z programu"
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
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b99b4f77f43f8ca9ac1516be2bf6a671810e7d90
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="2a557-102">Postupy: Vkládání elementů do textu z programu</span><span class="sxs-lookup"><span data-stu-id="2a557-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="2a557-103">Následující příklad ukazuje, jak používat dvě <xref:System.Windows.Documents.TextPointer> objekty, které chcete zadat rozsah v textu pro použití <xref:System.Windows.Documents.Span> element.</span><span class="sxs-lookup"><span data-stu-id="2a557-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a557-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a557-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="2a557-105">Následující obrázek ukazuje, jak vypadá v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="2a557-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="2a557-106">![Element Span použitý rozsah textu](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="2a557-106">![A Span element applied to a range of text](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a557-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a557-107">See Also</span></span>  
 [<span data-ttu-id="2a557-108">Přehled toku dokumentu</span><span class="sxs-lookup"><span data-stu-id="2a557-108">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
