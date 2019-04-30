---
title: 'Postupy: Implementace logiky ověření ve vlastních objektech'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931385"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="9bbb4-102">Postupy: Implementace logiky ověření ve vlastních objektech</span><span class="sxs-lookup"><span data-stu-id="9bbb4-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="9bbb4-103">Tento příklad ukazuje způsob implementace logiky ověření na vlastní objekt a připojit se k němu.</span><span class="sxs-lookup"><span data-stu-id="9bbb4-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbb4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bbb4-104">Example</span></span>  
 <span data-ttu-id="9bbb4-105">V obchodní vrstvě můžete poskytnout logiku ověřování, pokud zdrojový objekt implementuje <xref:System.ComponentModel.IDataErrorInfo>, jako v následujícím příkladu, který definuje `Person` objekt, který implementuje <xref:System.ComponentModel.IDataErrorInfo>:</span><span class="sxs-lookup"><span data-stu-id="9bbb4-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="9bbb4-106">V následujícím příkladu se vlastnost text textového pole vytvoří vazbu `Person.Age` vlastnosti, která je k dispozici pro vazbu prostřednictvím deklarace prostředků, která je přidělena `x:Key` `data`.</span><span class="sxs-lookup"><span data-stu-id="9bbb4-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="9bbb4-107"><xref:System.Windows.Controls.DataErrorValidationRule> Kontroluje výskyt chyb ověření vyvoláno <xref:System.ComponentModel.IDataErrorInfo> implementace.</span><span class="sxs-lookup"><span data-stu-id="9bbb4-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="9bbb4-108">Alternativně namísto použití <xref:System.Windows.Controls.DataErrorValidationRule>, můžete nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="9bbb4-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbb4-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bbb4-109">See also</span></span>

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [<span data-ttu-id="9bbb4-110">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="9bbb4-110">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="9bbb4-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9bbb4-111">How-to Topics</span></span>](data-binding-how-to-topics.md)
