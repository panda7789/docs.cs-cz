---
title: 'Postupy: Definice šablony GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910517"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="5d3f6-102">Postupy: Definice šablony GroupBox</span><span class="sxs-lookup"><span data-stu-id="5d3f6-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="5d3f6-103">Tento příklad ukazuje, jak vytvořit šablonu pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d3f6-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d3f6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d3f6-104">Example</span></span>  
 <span data-ttu-id="5d3f6-105">Následující příklad definuje <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku pomocí <xref:System.Windows.Controls.Grid> ovládací prvek pro rozložení.</span><span class="sxs-lookup"><span data-stu-id="5d3f6-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="5d3f6-106">Šablona používá <xref:System.Windows.Controls.BorderGapMaskConverter> definovat ohraničení <xref:System.Windows.Controls.GroupBox> tak, aby ohraničení není skryl <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> obsah.</span><span class="sxs-lookup"><span data-stu-id="5d3f6-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="5d3f6-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d3f6-107">See also</span></span>

- <xref:System.Windows.Controls.GroupBox>
- <span data-ttu-id="5d3f6-108">[Postupy: Vytvoření GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5d3f6-108">[How to: Create a GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span></span>
