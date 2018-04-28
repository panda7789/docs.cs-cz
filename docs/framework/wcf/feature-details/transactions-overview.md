---
title: Transakce ve Windows Communication Foundation – přehled
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76edd7cf30d9da06db6e0c2f4624bf9a6d677eca
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="1d9e4-102">Transakce ve Windows Communication Foundation – přehled</span><span class="sxs-lookup"><span data-stu-id="1d9e4-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="1d9e4-103">Transakce poskytují způsob k seskupení sady akcí nebo operací do jedné jednotky nedělitelných provádění.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="1d9e4-104">Transakce je soubor operací s následujícími vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="1d9e4-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="1d9e4-105">Nedělitelnost.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-105">Atomicity.</span></span> <span data-ttu-id="1d9e4-106">To zajišťuje, že buď všechny aktualizace byla dokončena v rámci konkrétní transakce se potvrdí a provedené trvanlivý nebo jsou všechny přerušena a vrácena zpět do jejich předchozího stavu.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="1d9e4-107">Konzistence.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-107">Consistency.</span></span> <span data-ttu-id="1d9e4-108">To zaručuje, že změny provedené v rámci transakce představují transformaci z jednoho konzistentního stavu do jiného.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="1d9e4-109">Například transakci, která převádí peníze z účtu kontroluje účet nezmění množství peníze na celkové bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="1d9e4-110">Izolace.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-110">Isolation.</span></span> <span data-ttu-id="1d9e4-111">Tím se zabrání transakce z sledování nepotvrzené změny, které patří do dalších souběžných transakcí.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="1d9e4-112">Izolace poskytuje abstrakci souběžnosti při zajišťovat jednu transakci nelze mít neočekávané dopad na provádění jiné transakci.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="1d9e4-113">Odolnost.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-113">Durability.</span></span> <span data-ttu-id="1d9e4-114">To znamená, že jakmile potvrzené, aktualizace spravované prostředky (například záznam databáze) bude trvalé při krátkodobém selhání.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="1d9e4-115"> poskytuje bohatou sadu funkcí, které vám umožní vytvořit distribuovaných transakcí v aplikace webové služby.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-115"> provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d9e4-116"> implementuje podporu pro protokol WS-AtomicTransaction (WS-AT), který umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace tok transakcí do umožňuje vzájemnou spolupráci aplikace, jako je například umožňuje vzájemnou spolupráci webové služby vytvořené pomocí jiných výrobců technologie.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-116"> implements support for the WS-AtomicTransaction (WS-AT) protocol that enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d9e4-117"> také implementuje podporu protokolu OLE transakce, který můžete použít ve scénářích, kde není nutné spolupráce funkci, která umožní toku transakcí.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-117"> also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="1d9e4-118">Konfigurační soubor aplikace můžete použít ke konfiguraci vazby na povolit nebo zakázat toku transakcí stejně jako nastavit požadovanou transakčního protokolu u vazby.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="1d9e4-119">Kromě toho můžete nastavit časové limity transakce na úrovni služby pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="1d9e4-120">Další informace najdete v tématu [povolení toku transakcí](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="1d9e4-120">For more information, see [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="1d9e4-121">Atributy transakce v <xref:System.ServiceModel> oboru názvů umožňují postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="1d9e4-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="1d9e4-122">Konfigurace transakce vypršení časových limitů a úroveň izolace filtrování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="1d9e4-123">Povolení funkce transakce a konfigurace pomocí chování dokončení transakce <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="1d9e4-124">Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributů na metodu kontrakt tak, aby vyžadovala, povolit nebo odepřít toku transakcí.</span><span class="sxs-lookup"><span data-stu-id="1d9e4-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="1d9e4-125">Další informace najdete v tématu [atributy transakce ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1d9e4-125">For more information, see [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9e4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d9e4-126">See Also</span></span>  
 [<span data-ttu-id="1d9e4-127">Atributy transakce ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1d9e4-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="1d9e4-128">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="1d9e4-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
