---
title: Vázání ovládacího prvku na typ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744987"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="248b3-102">Postupy: Vázání ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="248b3-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="248b3-103">Při vytváření ovládacích prvků, které komunikují s daty, někdy je nutné pro svázání ovládacího prvku s typem namísto objektu.</span><span class="sxs-lookup"><span data-stu-id="248b3-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="248b3-104">Tato situace nastane hlavně v době návrhu, pokud data nemusí být k dispozici, ale ovládací prvky vázané na data stále potřebují zobrazovat informace z veřejného rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="248b3-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="248b3-105">Například můžete navazovat ovládací prvek <xref:System.Windows.Forms.DataGridView> k objektu, který je vystavený webovou službou a chcete, aby ovládací prvek <xref:System.Windows.Forms.DataGridView> v době návrhu pokryl své sloupce s názvy členů vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="248b3-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="248b3-106">Ovládací prvek lze snadno navazovat na typ pomocí komponenty <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="248b3-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="248b3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="248b3-107">Example</span></span>  
 <span data-ttu-id="248b3-108">Následující příklad kódu ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> k vlastnímu typu pomocí komponenty <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="248b3-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="248b3-109">Když spustíte příklad, všimnete si, že <xref:System.Windows.Forms.DataGridView> má označené sloupce, které odráží vlastnosti objektu `Customer`, před tím, než se ovládací prvek naplní daty.</span><span class="sxs-lookup"><span data-stu-id="248b3-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="248b3-110">V příkladu je tlačítko Přidat zákazníka, které přidá data do ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="248b3-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="248b3-111">Po kliknutí na tlačítko se do <xref:System.Windows.Forms.BindingSource>přidá nový objekt `Customer`.</span><span class="sxs-lookup"><span data-stu-id="248b3-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="248b3-112">Ve scénáři reálného světa může být data získána voláním webové služby nebo jiného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="248b3-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="248b3-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="248b3-113">Compiling the Code</span></span>  
 <span data-ttu-id="248b3-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="248b3-114">This example requires:</span></span>  
  
- <span data-ttu-id="248b3-115">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="248b3-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248b3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="248b3-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="248b3-117">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="248b3-117">BindingSource Component</span></span>](bindingsource-component.md)
