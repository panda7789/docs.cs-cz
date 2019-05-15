---
title: 'Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 39beb5c7162fb01a51360330216687c158ff433c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583708"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="0511c-102">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="0511c-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="0511c-103">Některé zdroje dat pro ovládací prvky nevyvolávejte oznámení o změnách při změně, přidání nebo odstranění položek.</span><span class="sxs-lookup"><span data-stu-id="0511c-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="0511c-104">S <xref:System.Windows.Forms.BindingSource> součásti, můžete vytvořit vazbu k takovým zdrojům dat a vyvolání oznámení o změně v kódu.</span><span class="sxs-lookup"><span data-stu-id="0511c-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0511c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0511c-105">Example</span></span>  
 <span data-ttu-id="0511c-106">Tento formulář ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby seznam <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0511c-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0511c-107">V seznamu nevyvolává oznámení o změnách, proto <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodu na <xref:System.Windows.Forms.BindingSource> se volá při změně položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0511c-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="0511c-108">.</span><span class="sxs-lookup"><span data-stu-id="0511c-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0511c-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0511c-109">Compiling the Code</span></span>  
 <span data-ttu-id="0511c-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0511c-110">This example requires:</span></span>  
  
- <span data-ttu-id="0511c-111">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0511c-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0511c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0511c-112">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="0511c-113">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="0511c-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="0511c-114">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="0511c-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
