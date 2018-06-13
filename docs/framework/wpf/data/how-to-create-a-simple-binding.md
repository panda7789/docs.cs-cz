---
title: 'Postupy: Vytváření jednoduchých připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555015"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="84d47-102">Postupy: Vytváření jednoduchých připojení</span><span class="sxs-lookup"><span data-stu-id="84d47-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="84d47-103">Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="84d47-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84d47-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="84d47-104">Example</span></span>  
 <span data-ttu-id="84d47-105">V tomto příkladu jsou k dispozici `Person` objekt s řetězec vlastnost s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="84d47-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="84d47-106">`Person` Objekt je definován v oboru názvů názvem `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="84d47-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="84d47-107">Zvýrazněný řádek, který obsahuje `<src>` element v následujícím příkladu se vytvoří instance `Person` objektu s `PersonName` hodnota vlastnosti `Joe`.</span><span class="sxs-lookup"><span data-stu-id="84d47-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="84d47-108">To se provádí v `Resources` části a přiřazené `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="84d47-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="84d47-109">Zvýrazněný řádek, který obsahuje `<TextBlock>` element pak váže <xref:System.Windows.Controls.TextBlock> řídit k `PersonName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84d47-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="84d47-110">V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".</span><span class="sxs-lookup"><span data-stu-id="84d47-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d47-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="84d47-111">See Also</span></span>  
 [<span data-ttu-id="84d47-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="84d47-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="84d47-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="84d47-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
