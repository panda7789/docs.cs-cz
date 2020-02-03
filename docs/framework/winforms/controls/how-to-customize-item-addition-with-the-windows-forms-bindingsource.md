---
title: Přizpůsobení přidání položky pomocí komponenty BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738313"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="f43d5-102">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="f43d5-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="f43d5-103">Použijete-li <xref:System.Windows.Forms.BindingSource> komponentu k navázání ovládacího prvku model Windows Forms na zdroj dat, může být nutné pro přizpůsobení vytváření nových položek.</span><span class="sxs-lookup"><span data-stu-id="f43d5-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="f43d5-104">Komponenta <xref:System.Windows.Forms.BindingSource> to dělá tak, že poskytuje událost <xref:System.Windows.Forms.BindingSource.AddingNew>, která je obvykle vyvolána, když ovládací prvek musí vytvořit novou položku.</span><span class="sxs-lookup"><span data-stu-id="f43d5-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="f43d5-105">Vaše obslužná rutina události může poskytnout jakékoli vlastní chování (například volání metody webové služby nebo získání nového objektu z továrny tříd).</span><span class="sxs-lookup"><span data-stu-id="f43d5-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f43d5-106">Při přidání položky pomocí zpracování události <xref:System.Windows.Forms.BindingSource.AddingNew> nelze sčítání zrušit.</span><span class="sxs-lookup"><span data-stu-id="f43d5-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f43d5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f43d5-107">Example</span></span>  
 <span data-ttu-id="f43d5-108">Následující příklad ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> s objektem pro vytváření tříd pomocí komponenty <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="f43d5-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="f43d5-109">Když uživatel klikne na nový řádek ovládacího prvku <xref:System.Windows.Forms.DataGridView>, vyvolá se událost <xref:System.Windows.Forms.BindingSource.AddingNew>.</span><span class="sxs-lookup"><span data-stu-id="f43d5-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="f43d5-110">Obslužná rutina události vytvoří nový objekt `DemoCustomer`, který je přiřazen vlastnosti <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f43d5-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f43d5-111">Tím dojde k přidání nového objektu `DemoCustomer` do seznamu <xref:System.Windows.Forms.BindingSource> součásti a jeho zobrazení na novém řádku ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f43d5-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f43d5-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f43d5-112">Compiling the Code</span></span>  
 <span data-ttu-id="f43d5-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f43d5-113">This example requires:</span></span>  
  
- <span data-ttu-id="f43d5-114">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="f43d5-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43d5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f43d5-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="f43d5-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="f43d5-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f43d5-117">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="f43d5-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
