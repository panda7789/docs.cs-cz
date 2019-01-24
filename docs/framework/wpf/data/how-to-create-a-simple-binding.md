---
title: 'Postupy: Vytvoření jednoduchých připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 3e38fa5fd1c7d0a635efd93de6ebe551f1eb1b82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594834"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="04bfc-102">Postupy: Vytvoření jednoduchých připojení</span><span class="sxs-lookup"><span data-stu-id="04bfc-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="04bfc-103">Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="04bfc-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04bfc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04bfc-104">Example</span></span>  
 <span data-ttu-id="04bfc-105">V tomto příkladu je nutné `Person` objekt s řetězcovou vlastnost s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="04bfc-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="04bfc-106">`Person` Objekt je definovaný v oboru názvů volá `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="04bfc-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="04bfc-107">Zvýrazněný řádek, který obsahuje `<src>` element v následujícím příkladu vytvoří instanci `Person` objektu `PersonName` hodnotou vlastnosti `Joe`.</span><span class="sxs-lookup"><span data-stu-id="04bfc-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="04bfc-108">To se provádí v `Resources` části a přiřazené `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="04bfc-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="04bfc-109">Zvýrazněný řádek, který obsahuje `<TextBlock>` prvek pak vytvoří vazbu <xref:System.Windows.Controls.TextBlock> ovládací prvek `PersonName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="04bfc-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="04bfc-110">V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".</span><span class="sxs-lookup"><span data-stu-id="04bfc-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bfc-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04bfc-111">See also</span></span>
- [<span data-ttu-id="04bfc-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="04bfc-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="04bfc-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="04bfc-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
