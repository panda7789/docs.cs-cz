---
title: "Modely transakcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 782a6b5bdb206d285d619b8085993b591785aca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-models"></a><span data-ttu-id="8a5da-102">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="8a5da-102">Transaction Models</span></span>
<span data-ttu-id="8a5da-103">Toto téma popisuje vztah mezi programovací modely transakcí a součásti infrastruktury, které společnost Microsoft poskytuje.</span><span class="sxs-lookup"><span data-stu-id="8a5da-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="8a5da-104">Při použití transakcí v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je důležité si uvědomit, že jsou nevyberete mezi různými modely transakcí, ale spíš operační v různých úrovní integrované a konzistentní model.</span><span class="sxs-lookup"><span data-stu-id="8a5da-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="8a5da-105">Následující části popisují komponenty tři primární transakce.</span><span class="sxs-lookup"><span data-stu-id="8a5da-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="8a5da-106">Windows Communication Foundation transakce</span><span class="sxs-lookup"><span data-stu-id="8a5da-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="8a5da-107">Podpora transakcí v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje zápis transakční služeb.</span><span class="sxs-lookup"><span data-stu-id="8a5da-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="8a5da-108">Kromě toho s podporou pro protokol WS-AtomicTransaction (WS-AT), může aplikace tok transakcí webové služby vytvořené pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo technologie třetích stran.</span><span class="sxs-lookup"><span data-stu-id="8a5da-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="8a5da-109">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službě nebo aplikaci, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakce funkce poskytují atributy a konfigurace pro deklarativně určení jak a kdy infrastruktury by měl vytvářet, toku a synchronizovat transakce.</span><span class="sxs-lookup"><span data-stu-id="8a5da-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="8a5da-110">System.Transactions – transakce</span><span class="sxs-lookup"><span data-stu-id="8a5da-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="8a5da-111"><xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model na základě <xref:System.Transactions.Transaction> třídy, jakož i k implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třída, ve kterém infrastruktury automaticky spravuje transakce.</span><span class="sxs-lookup"><span data-stu-id="8a5da-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8a5da-112">Postup vytvoření transakční aplikace pomocí těchto dvou modelů najdete v tématu [zápis transakční aplikace](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="8a5da-112"> how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="8a5da-113">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službě nebo aplikaci, <xref:System.Transactions> poskytuje programovací model pro vytváření transakcí v rámci klientské aplikace a explicitně interakci s transakci, pokud jsou povinné, v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="8a5da-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="8a5da-114">Služba MSDTC transakce</span><span class="sxs-lookup"><span data-stu-id="8a5da-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="8a5da-115">Microsoft koordinátora pro distribuované transakce (MSDTC) je správce transakcí, která poskytuje podporu pro distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="8a5da-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="8a5da-116">[referenční informace pro programátory DTC](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="8a5da-116"> the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="8a5da-117">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby nebo aplikace, služby MSDTC poskytuje infrastrukturu pro koordinaci transakce vytvořené v rámci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="8a5da-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
