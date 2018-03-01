---
title: "BindingNavigator – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 921f8c7791620d51107fa2ff31a637094fc0c633
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bindingnavigator-control-overview-windows-forms"></a><span data-ttu-id="6283f-102">BindingNavigator – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6283f-102">BindingNavigator Control Overview (Windows Forms)</span></span>
<span data-ttu-id="6283f-103">Můžete použít <xref:System.Windows.Forms.BindingNavigator> řízení k vytvoření standardizovaným způsobem uživatelům vyhledávat a měnit data na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="6283f-103">You can use the <xref:System.Windows.Forms.BindingNavigator> control to create a standardized means for users to search and change data on a Windows Form.</span></span> <span data-ttu-id="6283f-104">Často používáte <xref:System.Windows.Forms.BindingNavigator> s <xref:System.Windows.Forms.BindingSource> komponenty, aby uživatelům pohyb záznamů dat ve formuláři a interakci s záznamy.</span><span class="sxs-lookup"><span data-stu-id="6283f-104">You frequently use <xref:System.Windows.Forms.BindingNavigator> with the <xref:System.Windows.Forms.BindingSource> component to enable users to move through data records on a form and interact with the records.</span></span>  
  
## <a name="how-the-bindingnavigator-works"></a><span data-ttu-id="6283f-105">Jak funguje BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="6283f-105">How the BindingNavigator Works</span></span>  
 <span data-ttu-id="6283f-106"><xref:System.Windows.Forms.BindingNavigator> Řízení se skládá z <xref:System.Windows.Forms.ToolStrip> s řadou <xref:System.Windows.Forms.ToolStripItem> objekty pro většinu běžné akce souvisejících s daty: přidání dat, odstranění dat a procházení data.</span><span class="sxs-lookup"><span data-stu-id="6283f-106">The <xref:System.Windows.Forms.BindingNavigator> control is composed of a <xref:System.Windows.Forms.ToolStrip> with a series of <xref:System.Windows.Forms.ToolStripItem> objects for most of the common data-related actions: adding data, deleting data, and navigating through data.</span></span> <span data-ttu-id="6283f-107">Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek obsahuje tyto standardní tlačítka.</span><span class="sxs-lookup"><span data-stu-id="6283f-107">By default, the <xref:System.Windows.Forms.BindingNavigator> control contains these standard buttons.</span></span> <span data-ttu-id="6283f-108">Zobrazuje snímek následující obrazovky <xref:System.Windows.Forms.BindingNavigator> prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="6283f-108">The following screen shot shows the <xref:System.Windows.Forms.BindingNavigator> control on a form.</span></span>  
  
 <span data-ttu-id="6283f-109">![BindingNavigator – ovládací prvek](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span><span class="sxs-lookup"><span data-stu-id="6283f-109">![BindingNavigator Control](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span></span>  
  
 <span data-ttu-id="6283f-110">V následující tabulce jsou uvedeny ovládací prvky a popisuje jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="6283f-110">The following table lists the controls and describes their functions.</span></span>  
  
|<span data-ttu-id="6283f-111">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6283f-111">Control</span></span>|<span data-ttu-id="6283f-112">Funkce</span><span class="sxs-lookup"><span data-stu-id="6283f-112">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="6283f-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> button</span></span>|<span data-ttu-id="6283f-114">Vloží nový řádek do základního datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="6283f-114">Inserts a new row into the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button</span></span>|<span data-ttu-id="6283f-116">Odstraní z podkladové zdroje dat na aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="6283f-116">Deletes the current row from the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button</span></span>|<span data-ttu-id="6283f-118">Přesun na první položku v podkladovém zdroji dat</span><span class="sxs-lookup"><span data-stu-id="6283f-118">Moves to the first item in the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> button</span></span>|<span data-ttu-id="6283f-120">Přejde na poslední položky v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6283f-120">Moves to the last item in the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> button</span></span>|<span data-ttu-id="6283f-122">Přesun na další položku v podkladovém zdroji dat</span><span class="sxs-lookup"><span data-stu-id="6283f-122">Moves to the next item in the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>tlačítko</span><span class="sxs-lookup"><span data-stu-id="6283f-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> button</span></span>|<span data-ttu-id="6283f-124">Přesune na předchozí položky v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6283f-124">Moves to the previous item in the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>textové pole</span><span class="sxs-lookup"><span data-stu-id="6283f-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> text box</span></span>|<span data-ttu-id="6283f-126">Vrátí aktuální pozici v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6283f-126">Returns the current position within the underlying data source.</span></span>|  
|<span data-ttu-id="6283f-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A>textové pole</span><span class="sxs-lookup"><span data-stu-id="6283f-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> text box</span></span>|<span data-ttu-id="6283f-128">Vrátí celkový počet položek v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6283f-128">Returns the total number of items in the underlying data source.</span></span>|  
  
 <span data-ttu-id="6283f-129">Pro každý ovládací prvek v této kolekci, je členem příslušné skupiny <xref:System.Windows.Forms.BindingSource> komponenty, která prostřednictvím kódu programu poskytuje stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="6283f-129">For each control in this collection, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically provides the same functionality.</span></span> <span data-ttu-id="6283f-130">Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> součásti, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6283f-130">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span>  
  
 <span data-ttu-id="6283f-131">Pokud výchozí tlačítka nejsou vhodné pro vaše aplikace, nebo pokud budete potřebovat další tlačítka pro podporu dalších typů funkce, můžete zadat vlastní <xref:System.Windows.Forms.ToolStrip> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="6283f-131">If the default buttons are not suited to your application, or if you require additional buttons to support other types of functionality, you can supply your own <xref:System.Windows.Forms.ToolStrip> buttons.</span></span> <span data-ttu-id="6283f-132">Viz také [postupy: Přidání načíst, uložit, a tlačítka Storno do ovládacího prvku Windows Forms BindingNavigator](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="6283f-132">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6283f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6283f-133">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="6283f-134">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="6283f-134">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
