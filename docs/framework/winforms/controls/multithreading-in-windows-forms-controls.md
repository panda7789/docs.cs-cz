---
title: "Podpora více vláken v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c4651ca9707dcf0fac2edea0f004275cfcf18cf2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="0c229-102">Podpora více vláken v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c229-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="0c229-103">V mnoha aplikacích můžete nastavit vaše uživatelské rozhraní (UI), které jsou rychlejšího provedením časově náročná operace na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="0c229-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="0c229-104">Počet nástroje jsou k dispozici pro multithreading vaše ovládací prvky Windows Forms, včetně <xref:System.Threading> obor názvů, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda a `BackgroundWorker` součásti.</span><span class="sxs-lookup"><span data-stu-id="0c229-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c229-105">`BackgroundWorker` Součást nahrazuje a přidá funkce <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda; však tyto se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="0c229-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0c229-106">Další informace najdete v tématu [BackgroundWorker – přehled komponenty](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0c229-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c229-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0c229-107">In This Section</span></span>  
 [<span data-ttu-id="0c229-108">Postupy: volání vláken ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c229-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="0c229-109">Ukazuje, jak provádět volání bezpečného přístupu do Windows Forms – ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="0c229-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="0c229-110">Postupy: použití vlákna na pozadí k vyhledávání souborů</span><span class="sxs-lookup"><span data-stu-id="0c229-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="0c229-111">Ukazuje, jak používat <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody na hledání souborů asynchronně.</span><span class="sxs-lookup"><span data-stu-id="0c229-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0c229-112">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0c229-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="0c229-113">Dokumenty komponentu, který zapouzdřuje pracovní vlákno pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="0c229-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="0c229-114">Obsahuje informace o tom, jak asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="0c229-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="0c229-115">Dokumenty jak načíst obrázek asynchronně.</span><span class="sxs-lookup"><span data-stu-id="0c229-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c229-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0c229-116">Related Sections</span></span>  
 [<span data-ttu-id="0c229-117">Postupy: spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="0c229-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="0c229-118">Ukazuje, jak provést časově náročná operace s <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="0c229-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="0c229-119">BackgroundWorker – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="0c229-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="0c229-120">Obsahuje témata, která popisují způsob použití <xref:System.ComponentModel.BackgroundWorker> součásti pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="0c229-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
