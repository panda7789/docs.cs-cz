---
title: Transakce aktivity v WF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6132f1d9cbeef3ed7af5d2b711d04e8bd5755bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="e9e05-102">Transakce aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="e9e05-102">Transaction Activities in WF</span></span>
<span data-ttu-id="e9e05-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Má několik poskytované systémem aktivity pro modelování transakce, kompenzace a zrušení.</span><span class="sxs-lookup"><span data-stu-id="e9e05-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="e9e05-104">Těchto programovacích modelů povolit v pracovním postupu pokračovat k dalšímu postupu v případě změny v obchodní logiku a zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="e9e05-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e9e05-105">transakce, kompenzace a zrušení, najdete v části [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md), a [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="e9e05-105"> transactions, compensation, and cancellation, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [Compensation](../../../docs/framework/windows-workflow-foundation/compensation.md), and [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="e9e05-106">Transakce aktivity</span><span class="sxs-lookup"><span data-stu-id="e9e05-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="e9e05-107">Zrušení logiku ve formě aktivity, přidruží hlavní cesta provádění také vyjádřený jako aktivita.</span><span class="sxs-lookup"><span data-stu-id="e9e05-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="e9e05-108">Podporuje kompenzace jeho podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e9e05-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="e9e05-109">Explicitně volá obslužnou rutinu kompenzace z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e9e05-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="e9e05-110">Explicitně volá obslužnou rutinu potvrzení z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e9e05-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="e9e05-111">Vymezuje pásma hranici transakce.</span><span class="sxs-lookup"><span data-stu-id="e9e05-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="e9e05-112">Obory životnost transakci, která se spouští pomocí přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9e05-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="e9e05-113">Transakce může plynoucích do pracovního postupu na inicializace zprávu nebo vytvoří dispečera, když doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9e05-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="e9e05-114">**Poznámka:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> se nachází v **zasílání zpráv** části **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="e9e05-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
