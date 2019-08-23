---
title: 'Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource'
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
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935353"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="9d70d-102">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="9d70d-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="9d70d-103">Použijete-li <xref:System.Windows.Forms.BindingSource> komponentu k navázání model Windows Formsho ovládacího prvku na zdroj dat, může být nutné pro přizpůsobení vytváření nových položek.</span><span class="sxs-lookup"><span data-stu-id="9d70d-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="9d70d-104">Komponenta to dělá tak, že <xref:System.Windows.Forms.BindingSource.AddingNew> poskytne událost, která je obvykle vyvolána, když ovládací prvek musí vytvořit novou položku. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="9d70d-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="9d70d-105">Vaše obslužná rutina události může poskytnout jakékoli vlastní chování (například volání metody webové služby nebo získání nového objektu z továrny tříd).</span><span class="sxs-lookup"><span data-stu-id="9d70d-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d70d-106">Při přidání položky pomocí zpracování <xref:System.Windows.Forms.BindingSource.AddingNew> události nelze sčítání zrušit.</span><span class="sxs-lookup"><span data-stu-id="9d70d-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d70d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d70d-107">Example</span></span>  
 <span data-ttu-id="9d70d-108">Následující příklad ukazuje, jak vytvořit vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku s objektem pro vytváření tříd <xref:System.Windows.Forms.BindingSource> pomocí komponenty.</span><span class="sxs-lookup"><span data-stu-id="9d70d-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="9d70d-109">Když uživatel klikne na <xref:System.Windows.Forms.DataGridView> nový řádek ovládacího prvku <xref:System.Windows.Forms.BindingSource.AddingNew> , vyvolá se událost.</span><span class="sxs-lookup"><span data-stu-id="9d70d-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="9d70d-110">Obslužná rutina události vytvoří nový `DemoCustomer` objekt, který je přiřazen <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9d70d-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9d70d-111">Tím dojde k přidání `DemoCustomer` nového objektu <xref:System.Windows.Forms.BindingSource> do seznamu komponent a k zobrazení v novém řádku <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9d70d-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d70d-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9d70d-112">Compiling the Code</span></span>  
 <span data-ttu-id="9d70d-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9d70d-113">This example requires:</span></span>  
  
- <span data-ttu-id="9d70d-114">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="9d70d-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d70d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d70d-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="9d70d-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="9d70d-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="9d70d-117">Postupy: Svázání ovládacího prvku model Windows Forms s typem</span><span class="sxs-lookup"><span data-stu-id="9d70d-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
