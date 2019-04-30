---
title: Výjimky, transakce a kompenzace
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774007"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="49e63-102">Výjimky, transakce a kompenzace</span><span class="sxs-lookup"><span data-stu-id="49e63-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="49e63-103">poskytuje několik různých mechanismy pro zpracování chyb za běhu v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="49e63-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="49e63-104">Pracovní postupy můžete použít kombinaci obslužné rutiny výjimek, zrušení, transakce a kompenzace ke zpracování a provést řádné zotavení chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="49e63-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49e63-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="49e63-105">In This Section</span></span>  
 [<span data-ttu-id="49e63-106">Výjimky</span><span class="sxs-lookup"><span data-stu-id="49e63-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="49e63-107">Popisuje způsob použití <xref:System.Activities.Statements.TryCatch> aktivity pro zpracování výjimek v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="49e63-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="49e63-108">Transakce</span><span class="sxs-lookup"><span data-stu-id="49e63-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="49e63-109">Popisuje způsob použití <xref:System.Activities.Statements.TransactionScope> aktivity pro použití transakcí v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="49e63-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="49e63-110">Kompenzace</span><span class="sxs-lookup"><span data-stu-id="49e63-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="49e63-111">Popisuje kompenzace v pracovních postupech a ukazuje, jak použít kompenzace aktivity, jako <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, a <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="49e63-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="49e63-112">Zrušení</span><span class="sxs-lookup"><span data-stu-id="49e63-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="49e63-113">Popisuje postup při zrušení zpracování v pracovní postupy pomocí integrovaných aktivit, stejně jako vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="49e63-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="49e63-114">Ladění pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="49e63-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="49e63-115">Popisuje, jak ladění pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="49e63-115">Describes how to debug workflows.</span></span>
