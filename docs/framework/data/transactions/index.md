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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5248dd3a4da450e411dd5d9a7843df6c9263026e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="ba5d5-102">Zpracování transakcí</span><span class="sxs-lookup"><span data-stu-id="ba5d5-102">Transaction Processing</span></span>
<span data-ttu-id="ba5d5-103">V případě zakoupení knihy online knihkupectví výměny se peníze (ve formě platební) pro knihy.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="ba5d5-104">Pokud váš kredit je dobré použít, řadu souvisejících operací zajišťuje, že získat knihy a knihkupectví získá vaše peníze.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="ba5d5-105">Nicméně pokud jedné operace v řadě dojde během serveru exchange, celý exchange se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="ba5d5-106">Nelze získat knihy a knihkupectví nebude mít k dispozici vaše peníze.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="ba5d5-107">Technologie odpovědné za výměnu vyváženého a předvídatelný se nazývá zpracování transakcí.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="ba5d5-108">Transakce zajistit, aby objektově orientované prostředky nejsou trvale aktualizována, není-li úspěšně dokončit všechny operace v rámci transakční jednotky.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="ba5d5-109">Kombinováním sadu souvisejících operací do jednotky, který je buď zcela úspěšná nebo zcela selže, můžete zjednodušit chyba obnovení a spolehlivost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="ba5d5-110">Systémy zpracování transakce se skládá z počítačového hardwaru a softwaru, který je hostitelem aplikace orientované transakce, která provede rutinní transakcí, které jsou nezbytné k podnikání.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="ba5d5-111">Příklady: systémy, které spravují prodejní objednávky položku, rezervace letenek, mezd, záznamy zaměstnanců, výrobní a příjemce.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="ba5d5-112">Tato část poskytuje obecné informace o zpracování transakcí a konkrétní informace o tom, jak napsat Transakční aplikace a správci prostředků pomocí rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba5d5-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ba5d5-113">In This Section</span></span>  
 [<span data-ttu-id="ba5d5-114">Základy transakce</span><span class="sxs-lookup"><span data-stu-id="ba5d5-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="ba5d5-115">Představuje základní transakce zpracování podmínky a konceptů.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="ba5d5-116">Funkce poskytované službou System.Transactions –</span><span class="sxs-lookup"><span data-stu-id="ba5d5-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="ba5d5-117">Popisuje, jak používat funkce v System.Transactions psát svůj vlastní transakční aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba5d5-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ba5d5-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="ba5d5-119">Poskytuje třídy, které umožňují váš kód k účasti v transakcích.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="ba5d5-120">Třídy podporu transakcí s více distribuované účastníky, několik fáze oznámení a trvalý zařazení.</span><span class="sxs-lookup"><span data-stu-id="ba5d5-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
