---
title: Modely transakcí
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050776"
---
# <a name="transaction-models"></a><span data-ttu-id="bfe1a-102">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="bfe1a-102">Transaction Models</span></span>
<span data-ttu-id="bfe1a-103">Toto téma popisuje vztah mezi programovací modely transakcí a komponent infrastruktury, které společnost Microsoft poskytuje.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="bfe1a-104">Při použití transakcí ve Windows Communication Foundation (WCF), je důležité pochopit, že se zrušením výběru možnosti mezi různými modely transakcí, ale místo toho provoz na různých úrovních integrované a konzistentní model.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="bfe1a-105">Následující části popisují tři komponenty primární transakce.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="bfe1a-106">Windows Communication Foundation transakce</span><span class="sxs-lookup"><span data-stu-id="bfe1a-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="bfe1a-107">Podpora transakcí v WCF umožňuje že zápis transakční služeb.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="bfe1a-108">Kromě toho s jeho podporu protokolu WS-AtomicTransaction (WS-AT), můžete aplikace tok transakcí, které webové služby vytvořené pomocí WCF nebo technologii jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="bfe1a-109">Ve službě WCF nebo aplikace poskytují funkce transakce WCF atributy a konfigurace pro deklarativně určení jak a kdy by měl vytvořit infrastrukturu, flow a synchronizovat transakce.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="bfe1a-110">Transakce System.Transactions</span><span class="sxs-lookup"><span data-stu-id="bfe1a-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="bfe1a-111"><xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model na základě <xref:System.Transactions.Transaction> třídy, jakož i jazyka implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třídy, ve kterém infrastruktury automaticky spravuje transakce.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="bfe1a-112">Další informace o tom, jak vytvořit transakční aplikaci pomocí těchto dvou modelech naleznete v tématu [zápis transakční aplikace](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="bfe1a-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="bfe1a-113">Ve službě WCF nebo aplikace <xref:System.Transactions> poskytuje programovací model pro vytváření transakcí v rámci klientské aplikace a explicitně interakci s transakcí, pokud jsou povinné, v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="bfe1a-114">Služba MSDTC transakcí</span><span class="sxs-lookup"><span data-stu-id="bfe1a-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="bfe1a-115">Microsoft distribuované transakce koordinátor MSDTC () je správce transakcí, která poskytuje podporu pro distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="bfe1a-116">Další informace najdete v tématu [DTC programátora](https://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="bfe1a-116">For more information, see the [DTC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="bfe1a-117">Ve službě WCF nebo aplikace služby MSDTC poskytuje infrastrukturu pro koordinaci transakce vytvořené v rámci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="bfe1a-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
