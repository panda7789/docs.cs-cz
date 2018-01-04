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
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="c14db-102">Podpora více vláken v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c14db-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="c14db-103">V mnoha aplikacích můžete nastavit vaše uživatelské rozhraní (UI), které jsou rychlejšího provedením časově náročná operace na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="c14db-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="c14db-104">Počet nástroje jsou k dispozici pro multithreading vaše ovládací prvky Windows Forms, včetně <xref:System.Threading> obor názvů, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda a `BackgroundWorker` součásti.</span><span class="sxs-lookup"><span data-stu-id="c14db-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c14db-105">`BackgroundWorker` Součást nahrazuje a přidá funkce <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda; však tyto se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="c14db-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c14db-106">Další informace najdete v tématu [BackgroundWorker – přehled komponenty](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c14db-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c14db-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c14db-107">In This Section</span></span>  
 [<span data-ttu-id="c14db-108">Postupy: Volání (bezpečná pro přístup z více vláken) ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c14db-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="c14db-109">Ukazuje, jak provádět volání bezpečného přístupu do Windows Forms – ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c14db-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c14db-110">Postupy: Použití vlákna na pozadí k vyhledávání souborů</span><span class="sxs-lookup"><span data-stu-id="c14db-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="c14db-111">Ukazuje, jak používat <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody na hledání souborů asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c14db-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c14db-112">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c14db-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c14db-113">Dokumenty komponentu, který zapouzdřuje pracovní vlákno pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c14db-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="c14db-114">Obsahuje informace o tom, jak asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="c14db-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="c14db-115">Dokumenty jak načíst obrázek asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c14db-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c14db-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c14db-116">Related Sections</span></span>  
 [<span data-ttu-id="c14db-117">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="c14db-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="c14db-118">Ukazuje, jak provést časově náročná operace s <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="c14db-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="c14db-119">Přehled komponenty BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="c14db-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="c14db-120">Obsahuje témata, která popisují způsob použití <xref:System.ComponentModel.BackgroundWorker> součásti pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c14db-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
