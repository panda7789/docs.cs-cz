---
title: Transakce ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: a8e3306612e016568ad7cfd5138ab538af771a17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585828"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="7135c-102">Transakce ve Windows Communication Foundation – přehled</span><span class="sxs-lookup"><span data-stu-id="7135c-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="7135c-103">Transakce poskytují způsob, jak seskupit sadu akcí nebo operací do jedné neoddělitelné jednotky spuštění.</span><span class="sxs-lookup"><span data-stu-id="7135c-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="7135c-104">Transakce je kolekce operací s následujícími vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="7135c-104">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="7135c-105">Atomicitu.</span><span class="sxs-lookup"><span data-stu-id="7135c-105">Atomicity.</span></span> <span data-ttu-id="7135c-106">Tím se zajistí, že všechny aktualizace dokončené v určité transakci jsou potvrzené a mají trvalé nebo všechny jsou přerušené a vrátí se zpátky do předchozího stavu.</span><span class="sxs-lookup"><span data-stu-id="7135c-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="7135c-107">Shody.</span><span class="sxs-lookup"><span data-stu-id="7135c-107">Consistency.</span></span> <span data-ttu-id="7135c-108">To zaručuje, že změny provedené v transakci reprezentují transformaci z jednoho konzistentního stavu na jiný.</span><span class="sxs-lookup"><span data-stu-id="7135c-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="7135c-109">Například transakce, která přenáší peníze z účtu pro kontrolu na účet úspory, nemění množství peněz v rámci celkového bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="7135c-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="7135c-110">Izolace.</span><span class="sxs-lookup"><span data-stu-id="7135c-110">Isolation.</span></span> <span data-ttu-id="7135c-111">To brání transakci v pozorování nepotvrzených změn, které patří do jiných souběžných transakcí.</span><span class="sxs-lookup"><span data-stu-id="7135c-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="7135c-112">Izolace poskytuje abstrakci souběžnosti a zároveň zajišťuje, že jedna transakce nemůže mít neočekávaný dopad na provedení jiné transakce.</span><span class="sxs-lookup"><span data-stu-id="7135c-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="7135c-113">Vlastností.</span><span class="sxs-lookup"><span data-stu-id="7135c-113">Durability.</span></span> <span data-ttu-id="7135c-114">To znamená, že po potvrzení budou aktualizace spravovaných prostředků (například záznamu v databázi) trvalé při selhání.</span><span class="sxs-lookup"><span data-stu-id="7135c-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="7135c-115">Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které umožňují vytvářet distribuované transakce v aplikaci webové služby.</span><span class="sxs-lookup"><span data-stu-id="7135c-115">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="7135c-116">Služba WCF implementuje podporu pro protokol WS-AtomicTransaction (WS-AT), který umožňuje aplikacím WCF tok transakcí do interoperabilních aplikací, jako jsou interoperabilní webové služby vytvořené pomocí technologie třetích stran.</span><span class="sxs-lookup"><span data-stu-id="7135c-116">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="7135c-117">WCF také implementuje podporu protokolu OLE Transactions, který může být použit ve scénářích, kde nepotřebujete funkce spolupráce, aby bylo možné tok transakcí povolit.</span><span class="sxs-lookup"><span data-stu-id="7135c-117">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="7135c-118">Konfigurační soubor aplikace můžete použít ke konfiguraci vazeb pro povolení nebo zakázání toku transakce a také k nastavení požadovaného transakčního protokolu pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7135c-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="7135c-119">Kromě toho můžete nastavit časový limit transakcí na úrovni služby pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7135c-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="7135c-120">Další informace najdete v tématu [Povolení toku transakce](enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="7135c-120">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="7135c-121">Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují následující akce:</span><span class="sxs-lookup"><span data-stu-id="7135c-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="7135c-122">Nakonfigurujte časové limity transakce a filtrování na úrovni izolace pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="7135c-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="7135c-123">Povolte funkce transakcí a nakonfigurujte chování při dokončování transakcí pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="7135c-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="7135c-124">Použijte <xref:System.ServiceModel.ServiceContractAttribute> atributy a <xref:System.ServiceModel.OperationContractAttribute> v metodě kontraktu pro vyžadování, povolení nebo zamítnutí toku transakce.</span><span class="sxs-lookup"><span data-stu-id="7135c-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="7135c-125">Další informace najdete v tématu [atributy transakce ServiceModel](servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7135c-125">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7135c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7135c-126">See also</span></span>

- [<span data-ttu-id="7135c-127">Atributy transakce ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7135c-127">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="7135c-128">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="7135c-128">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
