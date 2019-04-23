---
title: 'Postupy: Vytvoření jednoduché vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094382"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="9fc3e-102">Postupy: Vytvoření jednoduché vazby</span><span class="sxs-lookup"><span data-stu-id="9fc3e-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="9fc3e-103">Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fc3e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fc3e-104">Example</span></span>  
 <span data-ttu-id="9fc3e-105">V tomto příkladu je nutné `Person` objekt s řetězcovou vlastnost s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="9fc3e-106">`Person` Objekt je definovaný v oboru názvů volá `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="9fc3e-107">Zvýrazněný řádek, který obsahuje `<src>` element v následujícím příkladu vytvoří instanci `Person` objektu `PersonName` hodnotou vlastnosti `Joe`.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="9fc3e-108">To se provádí v `Resources` části a přiřazené `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="9fc3e-109">Zvýrazněný řádek, který obsahuje `<TextBlock>` prvek pak vytvoří vazbu <xref:System.Windows.Controls.TextBlock> ovládací prvek `PersonName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="9fc3e-110">V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".</span><span class="sxs-lookup"><span data-stu-id="9fc3e-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc3e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fc3e-111">See also</span></span>

- [<span data-ttu-id="9fc3e-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="9fc3e-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9fc3e-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9fc3e-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
