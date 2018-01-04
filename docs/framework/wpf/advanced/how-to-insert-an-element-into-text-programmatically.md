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
ms.workload: dotnet
ms.openlocfilehash: b200489c4b7fb06f2eb98c0ec9c84da42f18a395
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a>Postupy: Vkládání elementů do textu z programu
Následující příklad ukazuje, jak používat dvě <xref:System.Windows.Documents.TextPointer> objekty, které chcete zadat rozsah v textu pro použití <xref:System.Windows.Documents.Span> element.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 Následující obrázek ukazuje, jak vypadá v tomto příkladu.  
  
 ![Element Span použitý rozsah textu](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")  
  
## <a name="see-also"></a>Viz také  
 [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
