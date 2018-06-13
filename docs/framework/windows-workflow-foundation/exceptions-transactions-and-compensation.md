---
title: Výjimky transakce a kompenzace
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 346b07cd89c4071088676235d457930637b71549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512207"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="b31bd-102">Výjimky transakce a kompenzace</span><span class="sxs-lookup"><span data-stu-id="b31bd-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="b31bd-103"> poskytuje několik různých mechanismů pro nakládání běhu chybové stavy v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="b31bd-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="b31bd-104">Pracovní postupy můžete použít kombinaci obslužné rutiny výjimek, transakce, zrušení a náhrady ke zpracování a elegantně zotavit chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="b31bd-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b31bd-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b31bd-105">In This Section</span></span>  
 [<span data-ttu-id="b31bd-106">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b31bd-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="b31bd-107">Ukazuje, jak používat <xref:System.Activities.Statements.TryCatch> aktivity zpracování výjimek v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b31bd-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="b31bd-108">Transakce</span><span class="sxs-lookup"><span data-stu-id="b31bd-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="b31bd-109">Ukazuje, jak používat <xref:System.Activities.Statements.TransactionScope> aktivity pro použití transakcí v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b31bd-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="b31bd-110">Kompenzace</span><span class="sxs-lookup"><span data-stu-id="b31bd-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="b31bd-111">Popisuje kompenzace v pracovních postupech a ukazuje, jak pomocí aktivity kompenzace, jako například <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, a <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="b31bd-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="b31bd-112">Zrušení</span><span class="sxs-lookup"><span data-stu-id="b31bd-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="b31bd-113">Popisuje postup při zrušení zpracování v pracovních postupech, pomocí zabudované aktivity, jakož i vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="b31bd-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="b31bd-114">Ladění pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b31bd-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="b31bd-115">Popisuje, jak k ladění pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="b31bd-115">Describes how to debug workflows.</span></span>
