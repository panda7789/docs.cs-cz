---
title: BackgroundWorker – komponenta
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
ms.openlocfilehash: 0baf54d27cf33eef7e4df7019ee98b42eba40205
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710664"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="0f5c6-102">BackgroundWorker – komponenta</span><span class="sxs-lookup"><span data-stu-id="0f5c6-102">BackgroundWorker Component</span></span>
<span data-ttu-id="0f5c6-103">`BackgroundWorker` Komponenta povoluje formuláře nebo ovládacího prvku na spuštění operace asynchronně.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f5c6-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0f5c6-104">In This Section</span></span>  
 [<span data-ttu-id="0f5c6-105">Přehled komponenty BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="0f5c6-105">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="0f5c6-106">Popisuje `BackgroundWorker` součásti, která vám dává možnost provádět časově náročná operace asynchronně ("na pozadí"), ve vlákně, která se liší od hlavního vlákna uživatelského rozhraní vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="0f5c6-107">Návod: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f5c6-107">Walkthrough: Running an Operation in the Background</span></span>](walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="0f5c6-108">Popisuje způsob použití `BackgroundWorker` součásti v návrháři pro spuštění časově náročná operace na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="0f5c6-109">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f5c6-109">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="0f5c6-110">Popisuje způsob použití `BackgroundWorker` komponentu pro spuštění časově náročná operace na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="0f5c6-111">Návod: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f5c6-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="0f5c6-112">Vytvoří aplikaci s použitím návrháře, která provádí asynchronně matematických výpočtů.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="0f5c6-113">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f5c6-113">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="0f5c6-114">Vytvoří aplikaci, která provádí asynchronně matematických výpočtů.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="0f5c6-115">Postupy: Stahování souboru na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f5c6-115">How to: Download a File in the Background</span></span>](how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="0f5c6-116">Popisuje způsob použití `BackgroundWorker` součásti ke stažení souboru na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f5c6-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0f5c6-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="0f5c6-118">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="0f5c6-119">Popisuje typ, který obsahuje data pro <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="0f5c6-120">Popisuje typ, který obsahuje data pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f5c6-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0f5c6-121">Related Sections</span></span>  
 [<span data-ttu-id="0f5c6-122">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="0f5c6-122">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="0f5c6-123">Popisuje, jak asynchronního zpracování zpřístupní výhody vícevláknové aplikace při skrytí mnoho složitých problémů vyplývající vícevláknový návrhu.</span><span class="sxs-lookup"><span data-stu-id="0f5c6-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
