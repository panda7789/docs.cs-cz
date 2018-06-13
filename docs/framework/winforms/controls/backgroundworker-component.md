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
ms.openlocfilehash: 38505876e2f944139622a0d7cf7aaab9c510ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525749"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="a612c-102">BackgroundWorker – komponenta</span><span class="sxs-lookup"><span data-stu-id="a612c-102">BackgroundWorker Component</span></span>
<span data-ttu-id="a612c-103">`BackgroundWorker` Součást umožňuje formuláře nebo spuštění operace asynchronně ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a612c-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a612c-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a612c-104">In This Section</span></span>  
 [<span data-ttu-id="a612c-105">Přehled komponenty BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="a612c-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="a612c-106">Popisuje `BackgroundWorker` komponenta, která vám dává možnost provádět časově náročná operace asynchronně ("v pozadí"), na vlákno, která se liší od hlavního vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="a612c-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="a612c-107">Návod: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="a612c-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="a612c-108">Ukazuje, jak používat `BackgroundWorker` součásti v Návrháři ke spuštění časově náročná operace na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="a612c-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="a612c-109">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="a612c-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="a612c-110">Ukazuje, jak používat `BackgroundWorker` součásti spustit časově náročná operace na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="a612c-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="a612c-111">Návod: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="a612c-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="a612c-112">Vytvoří aplikace pomocí návrháře, která provádí matematické výpočty asynchronně.</span><span class="sxs-lookup"><span data-stu-id="a612c-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="a612c-113">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="a612c-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="a612c-114">Vytvoří aplikaci, která nemá matematické výpočty asynchronně.</span><span class="sxs-lookup"><span data-stu-id="a612c-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="a612c-115">Postupy: Stahování souboru na pozadí</span><span class="sxs-lookup"><span data-stu-id="a612c-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="a612c-116">Ukazuje, jak používat `BackgroundWorker` součásti ke stažení souboru na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="a612c-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a612c-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a612c-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a612c-118">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a612c-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="a612c-119">Popisuje typ, který obsahuje data <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="a612c-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="a612c-120">Popisuje typ, který obsahuje data <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="a612c-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a612c-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a612c-121">Related Sections</span></span>  
 [<span data-ttu-id="a612c-122">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="a612c-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="a612c-123">Popisuje, jak asynchronní vzor zpřístupní výhod vícevláknové aplikace při skrytí mnoho složitých problémů vyplývajících z více vláken návrhu.</span><span class="sxs-lookup"><span data-stu-id="a612c-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
