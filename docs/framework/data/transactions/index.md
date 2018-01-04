---
title: "Zpracování transakcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c66e982715d0f7f97e7a4faa92c2de57f3b1471
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="09ff7-102">Zpracování transakcí</span><span class="sxs-lookup"><span data-stu-id="09ff7-102">Transaction Processing</span></span>
<span data-ttu-id="09ff7-103">V případě zakoupení knihy online knihkupectví výměny se peníze (ve formě platební) pro knihy.</span><span class="sxs-lookup"><span data-stu-id="09ff7-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="09ff7-104">Pokud váš kredit je dobré použít, řadu souvisejících operací zajišťuje, že získat knihy a knihkupectví získá vaše peníze.</span><span class="sxs-lookup"><span data-stu-id="09ff7-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="09ff7-105">Nicméně pokud jedné operace v řadě dojde během serveru exchange, celý exchange se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="09ff7-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="09ff7-106">Nelze získat knihy a knihkupectví nebude mít k dispozici vaše peníze.</span><span class="sxs-lookup"><span data-stu-id="09ff7-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="09ff7-107">Technologie odpovědné za výměnu vyváženého a předvídatelný se nazývá zpracování transakcí.</span><span class="sxs-lookup"><span data-stu-id="09ff7-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="09ff7-108">Transakce zajistit, aby objektově orientované prostředky nejsou trvale aktualizována, není-li úspěšně dokončit všechny operace v rámci transakční jednotky.</span><span class="sxs-lookup"><span data-stu-id="09ff7-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="09ff7-109">Kombinováním sadu souvisejících operací do jednotky, který je buď zcela úspěšná nebo zcela selže, můžete zjednodušit chyba obnovení a spolehlivost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09ff7-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="09ff7-110">Systémy zpracování transakce se skládá z počítačového hardwaru a softwaru, který je hostitelem aplikace orientované transakce, která provede rutinní transakcí, které jsou nezbytné k podnikání.</span><span class="sxs-lookup"><span data-stu-id="09ff7-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="09ff7-111">Příklady: systémy, které spravují prodejní objednávky položku, rezervace letenek, mezd, záznamy zaměstnanců, výrobní a příjemce.</span><span class="sxs-lookup"><span data-stu-id="09ff7-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="09ff7-112">Tato část poskytuje obecné informace o zpracování transakcí a konkrétní informace o tom, jak napsat Transakční aplikace a správci prostředků pomocí rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09ff7-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09ff7-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="09ff7-113">In This Section</span></span>  
 [<span data-ttu-id="09ff7-114">Principy transakcí</span><span class="sxs-lookup"><span data-stu-id="09ff7-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="09ff7-115">Představuje základní transakce zpracování podmínky a konceptů.</span><span class="sxs-lookup"><span data-stu-id="09ff7-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="09ff7-116">Funkce poskytované přes System.Transactions</span><span class="sxs-lookup"><span data-stu-id="09ff7-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="09ff7-117">Popisuje, jak používat funkce v System.Transactions psát svůj vlastní transakční aplikace.</span><span class="sxs-lookup"><span data-stu-id="09ff7-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="09ff7-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="09ff7-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="09ff7-119">Poskytuje třídy, které umožňují váš kód k účasti v transakcích.</span><span class="sxs-lookup"><span data-stu-id="09ff7-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="09ff7-120">Třídy podporu transakcí s více distribuované účastníky, několik fáze oznámení a trvalý zařazení.</span><span class="sxs-lookup"><span data-stu-id="09ff7-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
