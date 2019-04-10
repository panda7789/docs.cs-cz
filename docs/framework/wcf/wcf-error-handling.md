---
title: Zpracování chyb WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: d70edacd2447fbe0b0b6db42b93f699ce7c17003
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306284"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="98fe6-102">Zpracování chyb WCF</span><span class="sxs-lookup"><span data-stu-id="98fe6-102">WCF Error Handling</span></span>
<span data-ttu-id="98fe6-103">Chyb zjištěných aplikací WCF patří do jedné ze tří skupin:</span><span class="sxs-lookup"><span data-stu-id="98fe6-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="98fe6-104">Chybám komunikace</span><span class="sxs-lookup"><span data-stu-id="98fe6-104">Communication Errors</span></span>  
  
2. <span data-ttu-id="98fe6-105">Chyby serveru proxy nebo kanálu</span><span class="sxs-lookup"><span data-stu-id="98fe6-105">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="98fe6-106">Chyby aplikace</span><span class="sxs-lookup"><span data-stu-id="98fe6-106">Application Errors</span></span>  
  
 <span data-ttu-id="98fe6-107">Pokud síť není k dispozici, klient použije nesprávnou adresu nebo hostitele služby není naslouchání pro příchozí zprávy dojít k chybám komunikace.</span><span class="sxs-lookup"><span data-stu-id="98fe6-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="98fe6-108">Chyby tohoto typu se vrátí ke klientovi jako <xref:System.ServiceModel.CommunicationException> nebo <xref:System.ServiceModel.CommunicationException>-odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="98fe6-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="98fe6-109">Proxy server nebo kanálu chyby jsou chyby, ke kterým dochází v rámci kanálu nebo proxy, samotného.</span><span class="sxs-lookup"><span data-stu-id="98fe6-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="98fe6-110">Zahrnout chyby tohoto typu: Pokus použít proxy server nebo kanálu, který bylo ukončeno, existuje neshoda kontraktů mezi klientem a službou nebo odmítají pověření klienta službou.</span><span class="sxs-lookup"><span data-stu-id="98fe6-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="98fe6-111">Existuje mnoho různých typů chyb v této kategorii pro zobrazení zde příliš mnoho.</span><span class="sxs-lookup"><span data-stu-id="98fe6-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="98fe6-112">Chyby tohoto typu se vrátí ke klientovi jako-je (na objektech výjimek není provedena žádná transformace).</span><span class="sxs-lookup"><span data-stu-id="98fe6-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="98fe6-113">Při provádění operace služby dojít k chybám aplikace.</span><span class="sxs-lookup"><span data-stu-id="98fe6-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="98fe6-114">Chyby tohoto druhu jsou odesílány ke klientovi jako <xref:System.ServiceModel.FaultException> nebo <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="98fe6-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="98fe6-115">Zpracování chyb v WCF provádí jeden nebo více z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="98fe6-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="98fe6-116">Přímo zpracování výjimky.</span><span class="sxs-lookup"><span data-stu-id="98fe6-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="98fe6-117">To je pouze pro komunikaci a chyby proxy nebo kanálu.</span><span class="sxs-lookup"><span data-stu-id="98fe6-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="98fe6-118">Použití kontraktů selhání</span><span class="sxs-lookup"><span data-stu-id="98fe6-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="98fe6-119">Implementace <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní</span><span class="sxs-lookup"><span data-stu-id="98fe6-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="98fe6-120">Zpracování <xref:System.ServiceModel.ServiceHost> události</span><span class="sxs-lookup"><span data-stu-id="98fe6-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="98fe6-121">Kontrakty selhání</span><span class="sxs-lookup"><span data-stu-id="98fe6-121">Fault Contracts</span></span>  
 <span data-ttu-id="98fe6-122">Kontrakty selhání umožňují definovat chyby, které se můžou objevit během operace služby na platformě nezávisle.</span><span class="sxs-lookup"><span data-stu-id="98fe6-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="98fe6-123">Ve výchozím nastavení budou vráceny všechny výjimky vyvolané z v rámci operace služby ke klientovi jako <xref:System.ServiceModel.FaultException> objektu.</span><span class="sxs-lookup"><span data-stu-id="98fe6-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="98fe6-124"><xref:System.ServiceModel.FaultException> Objekt bude obsahovat velmi málo informací.</span><span class="sxs-lookup"><span data-stu-id="98fe6-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="98fe6-125">Můžete určit informace o klientovi definováním kontrakt chyby a vrátí chyba jako <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="98fe6-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="98fe6-126">Další informace najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="98fe6-126">For more information, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="98fe6-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="98fe6-127">IErrorHandler</span></span>  
 <span data-ttu-id="98fe6-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> Rozhraní vám umožní větší kontrolu nad jak aplikaci WCF reagují na chyby.</span><span class="sxs-lookup"><span data-stu-id="98fe6-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="98fe6-129">Poskytuje plnou kontrolu nad chybová zpráva, která je vrácen do klienta a umožňuje provádět vlastní chyba při zpracování jako je například protokolování.</span><span class="sxs-lookup"><span data-stu-id="98fe6-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="98fe6-130">Další informace o <xref:System.ServiceModel.Dispatcher.IErrorHandler> a [rozšíří ovládací prvek průběhu zpracování chyb a vytváření sestav](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="98fe6-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="98fe6-131">ServiceHost Events</span><span class="sxs-lookup"><span data-stu-id="98fe6-131">ServiceHost Events</span></span>  
 <span data-ttu-id="98fe6-132"><xref:System.ServiceModel.ServiceHost> Třída hostitele služby a definuje několik událostí, které mohou být nezbytné pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="98fe6-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="98fe6-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="98fe6-133">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="98fe6-134">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="98fe6-134">For more information, see</span></span> <xref:System.ServiceModel.ServiceHost>
