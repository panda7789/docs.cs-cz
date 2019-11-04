---
title: 'Postupy: Vytváření jednoduchých připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453509"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="3df43-102">Postupy: Vytváření jednoduchých připojení</span><span class="sxs-lookup"><span data-stu-id="3df43-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="3df43-103">V tomto příkladu se dozvíte, jak vytvořit jednoduchý <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="3df43-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3df43-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3df43-104">Example</span></span>  
 <span data-ttu-id="3df43-105">V tomto příkladu máte objekt `Person` s vlastností řetězce s názvem `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="3df43-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="3df43-106">Objekt `Person` je definován v oboru názvů s názvem `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="3df43-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="3df43-107">Zvýrazněný řádek, který obsahuje prvek `<src>` v následujícím příkladu vytvoří instanci objektu `Person` s hodnotou vlastnosti `PersonName` `Joe`.</span><span class="sxs-lookup"><span data-stu-id="3df43-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="3df43-108">To se provádí v části `Resources` a přiřazená `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="3df43-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="3df43-109">Zvýrazněný řádek, který obsahuje prvek `<TextBlock>` poté sváže ovládací prvek <xref:System.Windows.Controls.TextBlock> s vlastností `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="3df43-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="3df43-110">V důsledku toho se <xref:System.Windows.Controls.TextBlock> zobrazí s hodnotou "Jana".</span><span class="sxs-lookup"><span data-stu-id="3df43-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df43-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3df43-111">See also</span></span>

- [<span data-ttu-id="3df43-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="3df43-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3df43-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3df43-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
