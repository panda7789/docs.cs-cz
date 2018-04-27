---
title: Vytváření aktivit pracovního postupu pomocí třídy aktivity
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 517e646c8a84ed4374c01da974d952d4f50a4e22
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="cab49-102">Vytváření aktivit pracovního postupu pomocí třídy aktivity</span><span class="sxs-lookup"><span data-stu-id="cab49-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="cab49-103">Nejzákladnější způsob, jak vytvořit aktivitu pomocí Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je vytvořte třídu, která dědí z <xref:System.Activities.Activity> vytvářející funkce sestavte vlastní aktivity nebo aktivity z [předdefinované Knihovna aktivit](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="cab49-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="cab49-104">Toto téma ukazuje, jak vytvořit aktivitu, která zapisuje dvě zprávy do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cab49-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="cab49-105">Chcete-li vytvořit vlastní aktivity pomocí Návrhář aktivity</span><span class="sxs-lookup"><span data-stu-id="cab49-105">To create a custom Activity using the activity designer</span></span>  
  
1.  <span data-ttu-id="cab49-106">Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cab49-106">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="cab49-107">Vyberte soubor, nový, projektu.</span><span class="sxs-lookup"><span data-stu-id="cab49-107">Select File, New, Project.</span></span> <span data-ttu-id="cab49-108">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="cab49-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="cab49-109">Vyberte **knihovna aktivit** v **šablony** okno.</span><span class="sxs-lookup"><span data-stu-id="cab49-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="cab49-110">Název nového projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="cab49-110">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="cab49-111">Otevřete novou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="cab49-111">Open the new activity.</span></span>  <span data-ttu-id="cab49-112">Přetáhněte <xref:System.Activities.Statements.Sequence> aktivity z panelu nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="cab49-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>  
  
4.  <span data-ttu-id="cab49-113">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="cab49-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="cab49-114">Zadejte `"Hello World"` (s uvozovky) do **Text** pole.</span><span class="sxs-lookup"><span data-stu-id="cab49-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>  
  
5.  <span data-ttu-id="cab49-115">Přetáhněte druhý <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence> aktivity pod první z nich.</span><span class="sxs-lookup"><span data-stu-id="cab49-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="cab49-116">Zadejte `"Goodbye"` (s uvozovky) do **Text** pole.</span><span class="sxs-lookup"><span data-stu-id="cab49-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
