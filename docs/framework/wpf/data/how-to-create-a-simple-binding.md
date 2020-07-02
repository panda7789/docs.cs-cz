---
title: 'Postupy: Vytváření jednoduchých připojení'
description: Pomocí tohoto postupu v Windows Presentation Foundation (WPF) vytvořte jednoduchou vazbu pro vaše aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618698"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="1f4e4-103">Postupy: Vytváření jednoduchých připojení</span><span class="sxs-lookup"><span data-stu-id="1f4e4-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="1f4e4-104">V tomto příkladu se dozvíte, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="1f4e4-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f4e4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f4e4-105">Example</span></span>  
 <span data-ttu-id="1f4e4-106">V tomto příkladu máte `Person` objekt s vlastností řetězce s názvem `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="1f4e4-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="1f4e4-107">`Person`Objekt je definován v oboru názvů s názvem `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="1f4e4-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="1f4e4-108">Zvýrazněný řádek, který obsahuje `<src>` prvek v následujícím příkladu, vytvoří instanci `Person` objektu s `PersonName` hodnotou vlastnosti `Joe` .</span><span class="sxs-lookup"><span data-stu-id="1f4e4-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="1f4e4-109">To se provádí v `Resources` oddílu a přiřazeno `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="1f4e4-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="1f4e4-110">Zvýrazněný řádek, který obsahuje `<TextBlock>` prvek, potom sváže <xref:System.Windows.Controls.TextBlock> ovládací prvek s `PersonName` vlastností.</span><span class="sxs-lookup"><span data-stu-id="1f4e4-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="1f4e4-111">Výsledkem je, že <xref:System.Windows.Controls.TextBlock> se zobrazí hodnota "Jana".</span><span class="sxs-lookup"><span data-stu-id="1f4e4-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4e4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f4e4-112">See also</span></span>

- [<span data-ttu-id="1f4e4-113">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="1f4e4-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1f4e4-114">– postupy</span><span class="sxs-lookup"><span data-stu-id="1f4e4-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
