---
title: Modely transakcí
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: d6c78a5342bf19d19308352cddc241f436bfcb3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745320"
---
# <a name="transaction-models"></a><span data-ttu-id="2c0bf-102">Modely transakcí</span><span class="sxs-lookup"><span data-stu-id="2c0bf-102">Transaction Models</span></span>
<span data-ttu-id="2c0bf-103">Toto téma popisuje vztah mezi modely programování transakcí a komponentami infrastruktury poskytované společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="2c0bf-104">Při použití transakcí v Windows Communication Foundation (WCF) je důležité pochopit, že mezi různými transakčními modely nemusíte vybírat, ale spíše pracujete v různých vrstvách integrovaného a konzistentního modelu.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="2c0bf-105">V následujících částech jsou popsány tři primární komponenty transakcí.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="2c0bf-106">Transakce Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2c0bf-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="2c0bf-107">Podpora transakcí v rámci WCF umožňuje psát transakční služby.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="2c0bf-108">Kromě toho s podporou protokolu WS-AtomicTransaction (WS-AT) můžou aplikace přesměrovat transakce na webové služby vytvořené pomocí WCF nebo technologie třetích stran.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="2c0bf-109">Ve službě nebo aplikaci WCF poskytují funkce transakcí WCF atributy a konfiguraci pro deklarativní určení, jak a kdy má infrastruktura vytvořit, flow a synchronizovat transakce.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="2c0bf-110">Transakce System. Transactions</span><span class="sxs-lookup"><span data-stu-id="2c0bf-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="2c0bf-111">Obor názvů <xref:System.Transactions> poskytuje explicitní programovací model založený na <xref:System.Transactions.Transaction> třídě a také implicitní programovací model pomocí třídy <xref:System.Transactions.TransactionScope>, ve které infrastruktura automaticky spravuje transakce.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="2c0bf-112">Další informace o tom, jak vytvořit transakční aplikaci pomocí těchto dvou modelů, najdete v tématu [zápis transakční aplikace](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="2c0bf-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="2c0bf-113">Ve službě nebo aplikaci WCF poskytuje <xref:System.Transactions> programovací model pro vytváření transakcí v rámci klientské aplikace a pro explicitní interakci s transakcí, pokud je to požadováno, v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="2c0bf-114">Transakce MSDTC</span><span class="sxs-lookup"><span data-stu-id="2c0bf-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="2c0bf-115">Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) je správce transakcí, který poskytuje podporu pro distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="2c0bf-116">Další informace najdete v referenční příručce [programátora DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2c0bf-116">For more information, see the [DTC Programmer's Reference](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="2c0bf-117">Ve službě nebo aplikaci WCF poskytuje služba MSDTC infrastrukturu pro koordinaci transakcí vytvořených v rámci klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="2c0bf-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
