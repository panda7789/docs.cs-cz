---
title: Transakce aktivity ve službě pracovního postupu
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714772"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="94a95-102">Transakce aktivity ve službě pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="94a95-102">Transaction Activities in WF</span></span>
<span data-ttu-id="94a95-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Má několik poskytované systémem aktivity pro modelování zrušení, transakce a kompenzace.</span><span class="sxs-lookup"><span data-stu-id="94a95-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="94a95-104">Těchto programovacích modelů povolit pracovní postup, pokračujte k dalšímu postupu v případě změny v obchodní logiku a zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="94a95-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="94a95-105">Další informace o zrušení, transakce a kompenzace najdete v tématu [transakce](workflow-transactions.md), [kompenzace](compensation.md), a [zrušení](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="94a95-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="94a95-106">Transakce aktivity</span><span class="sxs-lookup"><span data-stu-id="94a95-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="94a95-107">Přidruží zrušení logiky ve formuláři aktivity, hlavní cesta provádění, také vyjádřena jako aktivita.</span><span class="sxs-lookup"><span data-stu-id="94a95-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="94a95-108">Podporuje kompenzaci jeho podřízených aktivit.</span><span class="sxs-lookup"><span data-stu-id="94a95-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="94a95-109">Explicitně vyvolá obslužnou rutinu <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="94a95-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="94a95-110">Explicitně vyvolá obslužnou rutinu potvrzení <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="94a95-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="94a95-111">Vymezuje hranice transakce pásma.</span><span class="sxs-lookup"><span data-stu-id="94a95-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="94a95-112">Obory životnost transakce, která inicializuje přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="94a95-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="94a95-113">Transakce mohou byly převedeny do pracovního postupu na zahajující zprávu nebo vytvořené dispečer při doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="94a95-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="94a95-114">**Poznámka:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Se nachází v **zasílání zpráv** část **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="94a95-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
