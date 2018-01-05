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
ms.workload: dotnet
ms.openlocfilehash: 5044339e1d06bddad05151b2db99d5f96d068e77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Postupy: Implementace logiky ověření na vlastních objektech
Tento příklad ukazuje, jak implementovat logiku ověření na vlastní objekt a pak vytvořte vazbu na ni.  
  
## <a name="example"></a>Příklad  
 Je zdrojový objekt implementuje zadat logiku ověření na obchodní vrstvu <xref:System.ComponentModel.IDataErrorInfo>, jako v následujícím příkladu:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 V následujícím příkladu sváže vlastnosti textu textového pole `Age` vlastnost `Person` objekt, který byl zpřístupněn pro vazbu prostřednictvím deklaraci prostředku, který je uveden `x:Key``data`. <xref:System.Windows.Controls.DataErrorValidationRule> Zkontroluje chyby ověření aktivováno <xref:System.ComponentModel.IDataErrorInfo> implementace.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 Alternativně místo použití <xref:System.Windows.Controls.DataErrorValidationRule>, můžete nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [Implementace ověření vazby](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
