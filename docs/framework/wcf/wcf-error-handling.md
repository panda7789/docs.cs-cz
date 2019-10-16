---
title: Zpracování chyb WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 7e5c65da3fa13a3640c7a6948f1284d0c6ffdfc4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319933"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="9c0c8-102">Zpracování chyb WCF</span><span class="sxs-lookup"><span data-stu-id="9c0c8-102">WCF Error Handling</span></span>
<span data-ttu-id="9c0c8-103">Chyby zjištěné aplikací WCF patří do jedné ze tří skupin:</span><span class="sxs-lookup"><span data-stu-id="9c0c8-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="9c0c8-104">Chyby komunikace</span><span class="sxs-lookup"><span data-stu-id="9c0c8-104">Communication Errors</span></span>  
  
2. <span data-ttu-id="9c0c8-105">Chyby proxy/kanálu</span><span class="sxs-lookup"><span data-stu-id="9c0c8-105">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="9c0c8-106">Chyby aplikace</span><span class="sxs-lookup"><span data-stu-id="9c0c8-106">Application Errors</span></span>  
  
 <span data-ttu-id="9c0c8-107">K chybám komunikace dojde, když síť není k dispozici, klient používá nesprávnou adresu, nebo hostitel služby nenaslouchá příchozím zprávám.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="9c0c8-108">Chyby tohoto typu jsou vraceny klientovi jako <xref:System.ServiceModel.CommunicationException> nebo @no__t třídy odvozené od -1.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="9c0c8-109">Chyby proxy/kanálu jsou chyby, ke kterým dochází v rámci samotného kanálu nebo proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="9c0c8-110">Mezi chyby tohoto typu patří: pokus o použití proxy serveru nebo kanálu, který byl uzavřen, existuje neshoda kontraktu mezi klientem a službou nebo přihlašovací údaje klienta jsou službou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="9c0c8-111">Existuje mnoho různých typů chyb v této kategorii, takže seznam je příliš velký.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="9c0c8-112">Chyby tohoto typu jsou vraceny klientovi, jak je (žádná transformace není provedena na objektech výjimek).</span><span class="sxs-lookup"><span data-stu-id="9c0c8-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="9c0c8-113">Při provádění operace služby dojde k chybám aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="9c0c8-114">Chyby tohoto druhu jsou odesílány klientovi jako <xref:System.ServiceModel.FaultException> nebo <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="9c0c8-115">Zpracování chyb v WCF je prováděno jedním nebo více z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="9c0c8-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="9c0c8-116">Přímo se zpracovává vyvolaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="9c0c8-117">To se provádí jenom pro chyby komunikace a proxy/kanálu.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-117">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="9c0c8-118">Použití smluv o selhání</span><span class="sxs-lookup"><span data-stu-id="9c0c8-118">Using fault contracts</span></span>  
  
- <span data-ttu-id="9c0c8-119">Implementace rozhraní <xref:System.ServiceModel.Dispatcher.IErrorHandler></span><span class="sxs-lookup"><span data-stu-id="9c0c8-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="9c0c8-120">Zpracování událostí <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="9c0c8-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="9c0c8-121">Smlouvy o selhání</span><span class="sxs-lookup"><span data-stu-id="9c0c8-121">Fault Contracts</span></span>  
 <span data-ttu-id="9c0c8-122">Smlouvy o selhání umožňují definovat chyby, ke kterým může dojít během operace služby, a to nezávisle na platformě.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="9c0c8-123">Ve výchozím nastavení budou všechny výjimky vyvolané v rámci operace služby vráceny klientovi jako objekt <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="9c0c8-124">Objekt <xref:System.ServiceModel.FaultException> bude obsahovat velmi málo informací.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="9c0c8-125">Můžete řídit informace odesílané klientovi tak, že definujete kontrakt chyby a vrátíte chybu jako <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="9c0c8-126">Další informace najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="9c0c8-126">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="9c0c8-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="9c0c8-127">IErrorHandler</span></span>  
 <span data-ttu-id="9c0c8-128">Rozhraní <xref:System.ServiceModel.Dispatcher.IErrorHandler> umožňuje větší kontrolu nad tím, jak vaše aplikace WCF reaguje na chyby.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="9c0c8-129">Poskytuje plnou kontrolu nad chybovou zprávou vrácenou klientovi a umožňuje provádět vlastní zpracování chyb, jako je protokolování.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="9c0c8-130">Další informace o @no__t 0 a [rozšíření kontroly nad zpracováním chyb a vytváření sestav](./samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="9c0c8-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="9c0c8-131">Události ServiceHost</span><span class="sxs-lookup"><span data-stu-id="9c0c8-131">ServiceHost Events</span></span>  
 <span data-ttu-id="9c0c8-132">Třída <xref:System.ServiceModel.ServiceHost> hostuje služby a definuje několik událostí, které mohou být potřeba ke zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="9c0c8-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9c0c8-133">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="9c0c8-134">Další informace najdete v tématu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-134">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
