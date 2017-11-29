---
title: "Kanál potvrzení HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf8e62d99ffc0a7296d83685dfeb15993afff934
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="http-acknowledgement-channel"></a><span data-ttu-id="2e520-102">Kanál potvrzení HTTP</span><span class="sxs-lookup"><span data-stu-id="2e520-102">HTTP Acknowledgement Channel</span></span>
<span data-ttu-id="2e520-103">Kanál potvrzení HTTP je příkladem vrstveného kanálu, který změní jednosměrný vzorcem zasílání zpráv, povolení služby vědomí nebo odmítnout příchozí zprávy místo automaticky odesláno potvrzení na potvrzení.</span><span class="sxs-lookup"><span data-stu-id="2e520-103">The HTTP Acknowledgement Channel is an example of a layered channel that changes the one-way messaging pattern, allowing a service to acknowledge or refuse incoming messages rather than automatically sending an acknowledgement on receipt.</span></span> <span data-ttu-id="2e520-104">Kanál potvrzení HTTP také umožňuje službě potvrzení zpoždění, dokud mohl zajistit firemní úrovni záruku, že dojde ke zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="2e520-104">The HTTP Acknowledgement Channel also allows the service to delay acknowledgement until it can make a business-level guarantee that the message will be processed.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2e520-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="2e520-105">Demonstrates</span></span>  
 <span data-ttu-id="2e520-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Příklad vrstveného kanál (kanál potvrzení HTTP).</span><span class="sxs-lookup"><span data-stu-id="2e520-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Layered channel example (HTTP Acknowledgement channel).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2e520-107">Diskusní</span><span class="sxs-lookup"><span data-stu-id="2e520-107">Discussion</span></span>  
 <span data-ttu-id="2e520-108">Kanál potvrzení HTTP implementuje <xref:System.ServiceModel.Channels.ReceiveContext> ke změně tvaru požadavku a odpovědi HTTP o zasílání zpráv vzor jednosměrný vzor s zpožděné potvrzení.</span><span class="sxs-lookup"><span data-stu-id="2e520-108">The HTTP Acknowledgement Channel implements <xref:System.ServiceModel.Channels.ReceiveContext> to reshape the HTTP request-reply messaging pattern to a one-way pattern with delayed acknowledgement.</span></span> <span data-ttu-id="2e520-109">Pomocí této nové vzoru, služby můžete zajistit zpracování zprávy odesláním potvrzení ve formě stavový kód HTTP OK 200 bez blokování klienta, dokud dokončí zpracování zprávy nebo můžete odeslat zprávu selhání klientovi ve formátu protokolu HTTP Interní Server stavový kód chyby 500.</span><span class="sxs-lookup"><span data-stu-id="2e520-109">Using this new pattern, a service can ensure message processing by sending an acknowledgement in the form of an HTTP OK status code of 200 without blocking the client until message processing completes or can send a failure message to the client in the form of an HTTP Internal Server error status code of 500.</span></span> <span data-ttu-id="2e520-110">Například služby může odesílat potvrzení po napsání zprávu do fronty a poté pokračujte zpracování zprávy asynchronně.</span><span class="sxs-lookup"><span data-stu-id="2e520-110">For example, a service could send an acknowledgement after writing a message to a queue, and then continue processing the message asynchronously.</span></span> <span data-ttu-id="2e520-111">V tomto scénáři klienta může být jistí, že jeho zprávy se zpracuje alespoň jednou službou, pokud ji znovu odeslat každou zprávu, dokud ho potvrzení přijal od služby.</span><span class="sxs-lookup"><span data-stu-id="2e520-111">In this scenario, a client could be assured its messages were processed at least once by the service, if it re-sent each message until it received an acknowledgement from the service.</span></span> <span data-ttu-id="2e520-112">Všimněte si, že, pokud služba vyžaduje, aby rychlého asynchronní zprávu zpracování přes protokol HTTP, bez jakékoli zprávy zpracování záruky, pak se <xref:System.ServiceModel.Channels.OneWayBindingElement> je vhodnější volbou.</span><span class="sxs-lookup"><span data-stu-id="2e520-112">Note that, if a service requires fast asynchronous message processing over HTTP without any message processing guarantees, then the <xref:System.ServiceModel.Channels.OneWayBindingElement> is a more appropriate choice.</span></span>  
  
 <span data-ttu-id="2e520-113"><xref:System.ServiceModel.Channels.ReceiveContext>slouží k uchování zprávy na místě, když je zjištěno, zda může být zpráva zpracována na službu.</span><span class="sxs-lookup"><span data-stu-id="2e520-113"><xref:System.ServiceModel.Channels.ReceiveContext> is used to hold the message in place while it is determined whether the message can be processed at the service.</span></span> <span data-ttu-id="2e520-114">Uvedené schopnost služby úspěšně zpracovat zprávu voláním Complete na <xref:System.ServiceModel.Channels.ReceiveContext> objekt, který odesílá stavový kód HTTP OK a zda služba může zpracovat zprávu je indikován volání <xref:System.ServiceModel.Channels.ReceiveContext>na `Abandon` Metoda na <xref:System.ServiceModel.Channels.ReceiveContext> objekt, který odesílá chybový kód stavu HTTP interního serveru.</span><span class="sxs-lookup"><span data-stu-id="2e520-114">The ability of a service to successfully process the message is indicated by calling Complete on the <xref:System.ServiceModel.Channels.ReceiveContext> object that sends an HTTP OK status code and whether the service can process the message is indicated by calling <xref:System.ServiceModel.Channels.ReceiveContext>’s `Abandon` method on the <xref:System.ServiceModel.Channels.ReceiveContext> object, which sends an HTTP Internal Server error status code.</span></span>  
  
 <span data-ttu-id="2e520-115">V tomto příkladu klient požádá informace zpracování odesláním identifikátor zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="2e520-115">In this example, the client requests processing information by sending an employee ID.</span></span> <span data-ttu-id="2e520-116">Na konci služby Pokud ID zaměstnance přijatých je vyšší než 50, služba odesílá kód stavu HTTP 500 (vnitřní chyba serveru) zpět do klienta, jinak se předpokládá, že lze úspěšně provést zpracování a odešle kód stavu HTTP 200 ( Úspěšné) na klientovi.</span><span class="sxs-lookup"><span data-stu-id="2e520-116">On the service end, if the employee ID received is greater than 50, the service sends an HTTP Status code of 500 (Internal Server Error) back to the client, otherwise it is assumed that the processing can be successfully done and sends an HTTP Status code of 200 (Successful) to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e520-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="2e520-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2e520-118">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="2e520-118">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with Administrator privileges.</span></span>  
  
2.  <span data-ttu-id="2e520-119">Otevřete **HttpAckChannel** řešení.</span><span class="sxs-lookup"><span data-stu-id="2e520-119">Open the **HttpAckChannel** solution.</span></span>  
  
3.  <span data-ttu-id="2e520-120">Spusťte novou instanci třídy **služby** projektu kliknutím pravým tlačítkem na projekt v **Průzkumníku řešení**a výběr **ladění**, **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2e520-120">Start a new instance of the **Service** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, **Start new instance** from the context menu.</span></span>  
  
4.  <span data-ttu-id="2e520-121">Spusťte novou instanci třídy **klienta** projektu kliknutím pravým tlačítkem na projekt v **Průzkumníku řešení**a výběr **ladění**, a **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2e520-121">Start a new instance of the **Client** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, and **Start new instance** from the context menu.</span></span>  
  
5.  <span data-ttu-id="2e520-122">Jakmile služba spuštěna, stiskněte klávesu ENTER v okně klienta k odeslání zprávy do služby klienta.</span><span class="sxs-lookup"><span data-stu-id="2e520-122">Once the service has started, press ENTER in the client window to let the client send a message to the service.</span></span>  
  
6.  <span data-ttu-id="2e520-123">Zpracování první zprávu ve službě, a odešle stavový kód HTTP OK zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="2e520-123">The first message is processed on the service, and it sends an HTTP OK status code back to the client.</span></span>  
  
7.  <span data-ttu-id="2e520-124">O druhou zprávu úspěšná a odešle chybový kód stavu HTTP interního serveru zpět do klienta, které vyvolá <xref:System.ServiceModel.CommunicationException> na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="2e520-124">The second message is unsuccessful, and it sends an HTTP Internal Server error status code back to the client, which raises a <xref:System.ServiceModel.CommunicationException> on the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e520-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="2e520-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e520-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2e520-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e520-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2e520-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e520-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2e520-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
