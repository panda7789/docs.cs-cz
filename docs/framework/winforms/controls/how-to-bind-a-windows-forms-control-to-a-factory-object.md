---
title: Vázání ovládacího prvku na objekt factory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745092"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="0c01d-102">Postupy: Vázání ovládacího prvku Windows Forms k objektu factory</span><span class="sxs-lookup"><span data-stu-id="0c01d-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="0c01d-103">Při sestavování ovládacích prvků, které komunikují s daty, někdy budete potřebovat navázání ovládacího prvku na objekt nebo metodu, která generuje jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="0c01d-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="0c01d-104">Takový objekt nebo metoda se nazývá továrna.</span><span class="sxs-lookup"><span data-stu-id="0c01d-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="0c01d-105">Váš zdroj dat může být například návratovou hodnotou z volání metody, namísto objektu v paměti nebo typu.</span><span class="sxs-lookup"><span data-stu-id="0c01d-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="0c01d-106">Můžete navazovat ovládací prvek na tento druh zdroje dat, pokud zdroj vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="0c01d-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="0c01d-107">Ovládací prvek lze snadno navazovat na objekt továrny pomocí ovládacího prvku <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0c01d-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c01d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c01d-108">Example</span></span>  
 <span data-ttu-id="0c01d-109">Následující příklad ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> s metodou objektu pro vytváření pomocí ovládacího prvku <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0c01d-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="0c01d-110">Metoda Factory má název `GetOrdersByCustomerId`a vrátí všechny objednávky daného zákazníka v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="0c01d-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c01d-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0c01d-111">Compiling the Code</span></span>  
 <span data-ttu-id="0c01d-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0c01d-112">This example requires:</span></span>  
  
- <span data-ttu-id="0c01d-113">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="0c01d-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c01d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c01d-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="0c01d-115">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="0c01d-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="0c01d-116">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="0c01d-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
