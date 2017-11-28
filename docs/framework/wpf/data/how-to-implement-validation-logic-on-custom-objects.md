---
title: "Postupy: Implementace logiky ověření na vlastních objektech"
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
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41a995223742e21f3bcc32d23c21882ac7eef465
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="f7933-102">Postupy: Implementace logiky ověření na vlastních objektech</span><span class="sxs-lookup"><span data-stu-id="f7933-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="f7933-103">Tento příklad ukazuje, jak implementovat logiku ověření na vlastní objekt a pak vytvořte vazbu na ni.</span><span class="sxs-lookup"><span data-stu-id="f7933-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7933-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7933-104">Example</span></span>  
 <span data-ttu-id="f7933-105">Je zdrojový objekt implementuje zadat logiku ověření na obchodní vrstvu <xref:System.ComponentModel.IDataErrorInfo>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f7933-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="f7933-106">V následujícím příkladu sváže vlastnosti textu textového pole `Age` vlastnost `Person` objekt, který byl zpřístupněn pro vazbu prostřednictvím deklaraci prostředku, který je uveden `x:Key``data`.</span><span class="sxs-lookup"><span data-stu-id="f7933-106">In the following example, the text property of the text box binds to the `Age` property of the `Person` object, which has been made available for binding through a resource declaration that is given the `x:Key``data`.</span></span> <span data-ttu-id="f7933-107"><xref:System.Windows.Controls.DataErrorValidationRule> Zkontroluje chyby ověření aktivováno <xref:System.ComponentModel.IDataErrorInfo> implementace.</span><span class="sxs-lookup"><span data-stu-id="f7933-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 <span data-ttu-id="f7933-108">Alternativně místo použití <xref:System.Windows.Controls.DataErrorValidationRule>, můžete nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="f7933-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7933-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7933-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="f7933-110">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="f7933-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="f7933-111">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="f7933-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
