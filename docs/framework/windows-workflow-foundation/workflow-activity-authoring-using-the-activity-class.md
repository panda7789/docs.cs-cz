---
title: Vytváření aktivit pracovního postupu pomocí třídy Activity
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711860"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="c9071-102">Vytváření aktivit pracovního postupu pomocí třídy Activity</span><span class="sxs-lookup"><span data-stu-id="c9071-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="c9071-103">Základní způsob, jak vytvořit aktivity pomocí Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je vytvořit třídu, která dědí z <xref:System.Activities.Activity> , který vytvoří funkce sestavte vlastní aktivity nebo aktivity [integrované Knihovna aktivit](net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="c9071-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="c9071-104">Toto téma ukazuje, jak vytvořit aktivitu, která zapisuje dvě zprávy do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9071-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="c9071-105">Chcete-li vytvořit vlastní aktivitu pomocí návrháře aktivit</span><span class="sxs-lookup"><span data-stu-id="c9071-105">To create a custom Activity using the activity designer</span></span>

1.  <span data-ttu-id="c9071-106">Open Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c9071-106">Open Visual Studio 2012.</span></span>

2.  <span data-ttu-id="c9071-107">Vyberte soubor, nový, projekt.</span><span class="sxs-lookup"><span data-stu-id="c9071-107">Select File, New, Project.</span></span> <span data-ttu-id="c9071-108">Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu.</span><span class="sxs-lookup"><span data-stu-id="c9071-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="c9071-109">Vyberte **knihovny aktivit** v **šablony** okna.</span><span class="sxs-lookup"><span data-stu-id="c9071-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="c9071-110">Název nového projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="c9071-110">Name the new project HelloActivity.</span></span>

3.  <span data-ttu-id="c9071-111">Otevřete novou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="c9071-111">Open the new activity.</span></span>  <span data-ttu-id="c9071-112">Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu z panelu nástrojů na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="c9071-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4.  <span data-ttu-id="c9071-113">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9071-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="c9071-114">Zadejte `"Hello World"` (pomocí nabídky) do **Text** pole.</span><span class="sxs-lookup"><span data-stu-id="c9071-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5.  <span data-ttu-id="c9071-115">Přetáhněte druhý <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.Activities.Statements.Sequence> aktivitu pod první z nich.</span><span class="sxs-lookup"><span data-stu-id="c9071-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="c9071-116">Zadejte `"Goodbye"` (pomocí nabídky) do **Text** pole.</span><span class="sxs-lookup"><span data-stu-id="c9071-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
