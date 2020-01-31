---
title: Multithreading v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742140"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="312b9-102">Podpora více vláken v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="312b9-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="312b9-103">V mnoha aplikacích můžete své uživatelské rozhraní (UI) lépe reagovat tím, že provádíte časově náročné operace v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="312b9-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="312b9-104">K dispozici je řada nástrojů pro multithreading model Windows Forms ovládacích prvků, včetně oboru názvů <xref:System.Threading>, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody a součásti `BackgroundWorker`.</span><span class="sxs-lookup"><span data-stu-id="312b9-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="312b9-105">Komponenta `BackgroundWorker` nahrazuje a přidává funkce do oboru názvů <xref:System.Threading> a do metody <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>; jsou ale zachovaná pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="312b9-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="312b9-106">Další informace najdete v tématu [Přehled komponent BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="312b9-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="312b9-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="312b9-107">In This Section</span></span>  
 [<span data-ttu-id="312b9-108">Postupy: Volání (bezpečná pro přístup z více vláken) ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="312b9-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="312b9-109">Ukazuje, jak učinit volání bezpečná pro přístup z více vláken na ovládací prvky model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="312b9-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="312b9-110">Postupy: Použití vlákna na pozadí k vyhledávání souborů</span><span class="sxs-lookup"><span data-stu-id="312b9-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="312b9-111">Ukazuje, jak použít <xref:System.Threading> obor názvů a metodu <xref:System.Windows.Forms.Control.BeginInvoke%2A> pro asynchronní hledání souborů.</span><span class="sxs-lookup"><span data-stu-id="312b9-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="312b9-112">Odkaz</span><span class="sxs-lookup"><span data-stu-id="312b9-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="312b9-113">Dokumentuje komponentu, která zapouzdřuje pracovní vlákno pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="312b9-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="312b9-114">Dokumentuje asynchronní načítání zvuku.</span><span class="sxs-lookup"><span data-stu-id="312b9-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="312b9-115">Dokumentuje asynchronní načtení obrázku.</span><span class="sxs-lookup"><span data-stu-id="312b9-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="312b9-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="312b9-116">Related Sections</span></span>  
 [<span data-ttu-id="312b9-117">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="312b9-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="312b9-118">Ukazuje, jak provést časově náročnou operaci s <xref:System.ComponentModel.BackgroundWorker> komponentou.</span><span class="sxs-lookup"><span data-stu-id="312b9-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="312b9-119">Přehled komponenty BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="312b9-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="312b9-120">Poskytuje témata, které popisují, jak používat součást <xref:System.ComponentModel.BackgroundWorker> pro asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="312b9-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
