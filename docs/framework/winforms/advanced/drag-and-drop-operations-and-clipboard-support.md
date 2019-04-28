---
title: Operace přetažení a podpora schránky
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 5e7bb75b648163dab7e410a159d55ebbb75f1b0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756426"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="8ffa7-102">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="8ffa7-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="8ffa7-103">Operace přetažení myší uživatelů v rámci aplikace založené na Windows můžete povolit řeší řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="8ffa7-104">Můžete také implementovat podporu vyjmutí/zkopírování/vložení uživatele a uživatelská data přenášet do schránky. v rámci vaší aplikace pro systém Windows pomocí jednoduchý způsob volání.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ffa7-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8ffa7-105">In This Section</span></span>  
 [<span data-ttu-id="8ffa7-106">Návod: Operace a přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ffa7-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="8ffa7-107">Vysvětluje, jak spustit operaci přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="8ffa7-108">Postupy: Provádění operací přetažení myší mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="8ffa7-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="8ffa7-109">Ukazuje, jak k provádění operací přetažení myší napříč aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="8ffa7-110">Postupy: Přidání dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-110">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="8ffa7-111">Popisuje způsob, jak prostřednictvím kódu programu vložení informací do schránky.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="8ffa7-112">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="8ffa7-112">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="8ffa7-113">Popisuje, jak přístup k datům uloženým ve schránce.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ffa7-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8ffa7-114">Related Sections</span></span>  
 [<span data-ttu-id="8ffa7-115">Funkce přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ffa7-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="8ffa7-116">Popisuje metody, události a třídy používané k implementaci chování a přetažení.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="8ffa7-117">Popisuje složitými rozhraními události, která žádá oprávnění pokračovat v provádění operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="8ffa7-118">Popisuje složitými rozhraními metody, která je zásadním zahájení operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="8ffa7-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="8ffa7-119">Viz také [jak: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="8ffa7-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>
