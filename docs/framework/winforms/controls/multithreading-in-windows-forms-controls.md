---
title: Podpora více vláken v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703319"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="8e58e-102">Podpora více vláken v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e58e-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="8e58e-103">V mnoha aplikacích můžete provést uživatelského rozhraní (UI), které jsou rychlejší reakce provedením časově náročných operací v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="8e58e-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="8e58e-104">Různé nástroje jsou k dispozici pro multithreading své ovládací prvky Windows Forms, včetně <xref:System.Threading> obor názvů, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody a `BackgroundWorker` komponenty.</span><span class="sxs-lookup"><span data-stu-id="8e58e-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e58e-105">`BackgroundWorker` Komponenty nahradí a přidá funkce, které <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metoda; ale ty se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="8e58e-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8e58e-106">Další informace najdete v tématu [přehled komponenty BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8e58e-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e58e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8e58e-107">In This Section</span></span>  
 [<span data-ttu-id="8e58e-108">Postupy: Bezpečné pro vlákna volání ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e58e-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="8e58e-109">Ukazuje, jak provádět volání bezpečným pro vlákno pro ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8e58e-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="8e58e-110">Postupy: Použití vlákna na pozadí k vyhledávání souborů</span><span class="sxs-lookup"><span data-stu-id="8e58e-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="8e58e-111">Ukazuje způsob použití <xref:System.Threading> obor názvů a <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody k vyhledání souborů asynchronně.</span><span class="sxs-lookup"><span data-stu-id="8e58e-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8e58e-112">Odkaz</span><span class="sxs-lookup"><span data-stu-id="8e58e-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="8e58e-113">Dokumenty komponenty, která zapouzdřuje pracovní vlákno pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="8e58e-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="8e58e-114">Popisem asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="8e58e-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="8e58e-115">Dokumenty o načtení obrázku asynchronně.</span><span class="sxs-lookup"><span data-stu-id="8e58e-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e58e-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8e58e-116">Related Sections</span></span>  
 [<span data-ttu-id="8e58e-117">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="8e58e-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="8e58e-118">Ukazuje, jak provádět časově náročná operace s <xref:System.ComponentModel.BackgroundWorker> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8e58e-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="8e58e-119">Přehled komponenty BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="8e58e-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="8e58e-120">Obsahuje témata, které popisují způsob použití <xref:System.ComponentModel.BackgroundWorker> komponenty pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="8e58e-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
