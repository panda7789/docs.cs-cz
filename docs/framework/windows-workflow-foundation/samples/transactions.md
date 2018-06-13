---
title: Transactions2
ms.date: 03/30/2017
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
ms.openlocfilehash: 361022851d971c0b9350899e1fee6a27c557d666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514592"
---
# <a name="transactions"></a><span data-ttu-id="d0384-102">Transakce</span><span class="sxs-lookup"><span data-stu-id="d0384-102">Transactions</span></span>
<span data-ttu-id="d0384-103">Tato část obsahuje ukázky, která ukazují pracovní postup transakce ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="d0384-103">This section contains samples that demonstrate workflow transactions in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0384-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d0384-104">In This Section</span></span>  
 [<span data-ttu-id="d0384-105">Základní TransactionScope</span><span class="sxs-lookup"><span data-stu-id="d0384-105">Basic TransactionScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 <span data-ttu-id="d0384-106">Se skládá ze čtyř scénáře, které ukazují, jak lze vnořit <xref:System.Activities.Statements.TransactionScope> instance.</span><span class="sxs-lookup"><span data-stu-id="d0384-106">Consists of four scenarios that show how to nest <xref:System.Activities.Statements.TransactionScope> instances.</span></span>  
  
 [<span data-ttu-id="d0384-107">Použití TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="d0384-107">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 <span data-ttu-id="d0384-108">Ukazuje, jak toku transakce z klienta na server pomocí <xref:System.Activities.Statements.TransactionScope> vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> přijmout zprávu s sdružení transakcí a obor životnost transakce na serveru.</span><span class="sxs-lookup"><span data-stu-id="d0384-108">Demonstrates how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span>  
  
 [<span data-ttu-id="d0384-109">Vnoření TransactionScope do služby</span><span class="sxs-lookup"><span data-stu-id="d0384-109">Nesting of TransactionScope within a service</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 <span data-ttu-id="d0384-110">Se skládá z těchto dvou scénářů, které ukazují, jak zpracovat <xref:System.Activities.Statements.TransactionScope> instance aktivit v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="d0384-110">Consists of two scenarios that show how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span>
