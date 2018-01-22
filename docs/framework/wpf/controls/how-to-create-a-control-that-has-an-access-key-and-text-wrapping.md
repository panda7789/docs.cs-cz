---
title: "Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8ef62b06e97e5db22fde0085e21d7a998bfdf22
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="98d72-102">Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu</span><span class="sxs-lookup"><span data-stu-id="98d72-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="98d72-103">Tento příklad ukazuje postup vytvoření ovládacího prvku, který má přístupový klíč a podporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="98d72-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="98d72-104">V příkladu se používá <xref:System.Windows.Controls.Label> ovládací prvek pro ilustraci tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="98d72-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98d72-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="98d72-105">Example</span></span>  
 <span data-ttu-id="98d72-106">**Přidat do vaší popisek zalamování textu**</span><span class="sxs-lookup"><span data-stu-id="98d72-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="98d72-107"><xref:System.Windows.Controls.Label> Ovládací prvek nepodporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="98d72-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="98d72-108">Pokud potřebujete zalomen na více řádcích štítek, můžete vnořovat jiné element, který podporuje text zabalení a umístí prvku v popisku.</span><span class="sxs-lookup"><span data-stu-id="98d72-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="98d72-109">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.TextBlock> aby štítek, který zahrnuje několik řádků textu.</span><span class="sxs-lookup"><span data-stu-id="98d72-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="98d72-110">**Přidat přístupový klíč a zalamování textu na vaše štítek**</span><span class="sxs-lookup"><span data-stu-id="98d72-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="98d72-111">Pokud potřebujete <xref:System.Windows.Controls.Label> s přístupový klíč (symbol), použijte <xref:System.Windows.Controls.AccessText> element, který je uvnitř <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="98d72-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="98d72-112">Ovládací prvky jako například <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, a <xref:System.Windows.Controls.GroupBox> žádné výchozí šablony ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="98d72-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="98d72-113">Tyto šablony obsahovat <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="98d72-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="98d72-114">Jedna z vlastností, které můžete nastavit <xref:System.Windows.Controls.ContentPresenter> je <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", který můžete použít k určení přístupový klíč pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="98d72-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="98d72-115">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Label> , který má přístupový klíč a podporuje zalamování textu.</span><span class="sxs-lookup"><span data-stu-id="98d72-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="98d72-116">K povolení zalamování textu, v příkladu je nastavena <xref:System.Windows.Controls.AccessText.TextWrapping%2A> vlastnost a používá znak podtržení, které pokud chcete zadat přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="98d72-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="98d72-117">(Znak, který následuje znak podtržení se přístupový klíč.)</span><span class="sxs-lookup"><span data-stu-id="98d72-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="98d72-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="98d72-118">See Also</span></span>  
 [<span data-ttu-id="98d72-119">Postupy: nastavte vlastnost Target tohoto štítku</span><span class="sxs-lookup"><span data-stu-id="98d72-119">How to: Set the Target Property of a Label</span></span>](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
