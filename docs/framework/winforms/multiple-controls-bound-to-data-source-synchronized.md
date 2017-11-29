---
title: "Postupy: Zajistěte, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2573f342530e59fa05e7f24342f251990b2ce47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="7cede-102">Postupy: Zajistěte, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="7cede-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="7cede-103">Často při práci s datové vazby v systému Windows Forms, jsou svázané více ovládacích prvků na stejném datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="7cede-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="7cede-104">V některých případech může být nutné provést další kroky k zajištění, aby zůstaly synchronizované s sebe navzájem a zdroj dat vázané vlastnosti ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7cede-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="7cede-105">Tyto kroky jsou nutné ve dvou situacích:</span><span class="sxs-lookup"><span data-stu-id="7cede-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="7cede-106">Pokud zdroj dat neimplementuje <xref:System.ComponentModel.IBindingList>a proto generování <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span><span class="sxs-lookup"><span data-stu-id="7cede-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="7cede-107">Pokud zdroj dat implementuje <xref:System.ComponentModel.IEditableObject>.</span><span class="sxs-lookup"><span data-stu-id="7cede-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="7cede-108">V prvním případě můžete použít <xref:System.Windows.Forms.BindingSource> svázat zdroj dat pro ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7cede-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="7cede-109">V takovém případě použijete <xref:System.Windows.Forms.BindingSource> a zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a volání <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> na přidruženého <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="7cede-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cede-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cede-110">Example</span></span>  
 <span data-ttu-id="7cede-111">Následující příklad kódu ukazuje, jak k vytvoření vazby ovládacích prvků tři – dvou ovládacích prvků textového pole a <xref:System.Windows.Forms.DataGridView> ovládací prvek – na stejný sloupec v <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="7cede-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="7cede-112">Tento příklad ukazuje, jak bude zpracováván <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a ověřte, že při změně textové hodnoty jednoho textového pole, další textového pole a <xref:System.Windows.Forms.DataGridView> řízení jsou aktualizovány pomocí správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7cede-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="7cede-113">V příkladu se používá <xref:System.Windows.Forms.BindingSource> k vytvoření vazby zdroje dat a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7cede-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="7cede-114">Alternativně můžete vytvoření vazby ovládacích prvků přímo ke zdroji dat a načtení <xref:System.Windows.Forms.BindingManagerBase> pro vazbu z formuláře <xref:System.Windows.Forms.Control.BindingContext%2A> a pak zpracovat <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> událost pro <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="7cede-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="7cede-115">Příklad toho, jak to provést naleznete na stránce nápovědy <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> události <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="7cede-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7cede-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7cede-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7cede-117">Tento příklad kódu vyžaduje</span><span class="sxs-lookup"><span data-stu-id="7cede-117">This code example requires</span></span>  
  
-   <span data-ttu-id="7cede-118">Odkazuje na <xref:System>, <xref:System.Windows.Forms>, a <xref:System.Drawing> sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cede-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="7cede-119">Formulář s <xref:System.Windows.Forms.Form.Load> zpracovává události a volání `InitializeControlsAndDataSource` metoda v příkladu z formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7cede-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cede-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cede-120">See Also</span></span>  
 [<span data-ttu-id="7cede-121">Postupy: sdílení připojených dat mezi formuláři pomocí součásti BindingSource</span><span class="sxs-lookup"><span data-stu-id="7cede-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="7cede-122">Oznámení změn v systému Windows Forms datové vazby</span><span class="sxs-lookup"><span data-stu-id="7cede-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="7cede-123">Rozhraní související s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="7cede-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="7cede-124">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="7cede-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
