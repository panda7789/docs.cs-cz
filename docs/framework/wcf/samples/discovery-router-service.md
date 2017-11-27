---
title: "Služba zjišťování směrovačů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 663ece44a18ae073412376bc11a1d70927740e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-router-service"></a><span data-ttu-id="28327-102">Služba zjišťování směrovačů</span><span class="sxs-lookup"><span data-stu-id="28327-102">Discovery Router Service</span></span>
<span data-ttu-id="28327-103">Tento příklad znázorňuje způsob zjišťování zprávy předány jiný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28327-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="28327-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="28327-104">Demonstrates</span></span>  
 <span data-ttu-id="28327-105">Zjišťování směrování</span><span class="sxs-lookup"><span data-stu-id="28327-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="28327-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="28327-106">Discussion</span></span>  
 <span data-ttu-id="28327-107">Zjišťování směrování je užitečné v scénář, ve kterém klient hledá služby pomocí proxy serveru a proxy server nemá informace o těchto služeb, ale zná jiné proxy.</span><span class="sxs-lookup"><span data-stu-id="28327-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="28327-108">Tento proxy server může předat paket zjišťování od tohoto klienta na druhý server proxy.</span><span class="sxs-lookup"><span data-stu-id="28327-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="28327-109">Druhý proxy server můžete vyhledejte službu a vrátit odpovědí na původní klienta.</span><span class="sxs-lookup"><span data-stu-id="28327-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="28327-110">V této ukázce klient odešle zprávu do směrování součást zjišťování.</span><span class="sxs-lookup"><span data-stu-id="28327-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="28327-111">Tato zpráva je odeslána na konkrétní na směrovači zjišťování.</span><span class="sxs-lookup"><span data-stu-id="28327-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="28327-112">Směrovač pak předá zprávu UDP vícesměrového vysílání koncový bod.</span><span class="sxs-lookup"><span data-stu-id="28327-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="28327-113">Test zprávy nedostane mimo vícesměrového vysílání koncový bod a službu nenaslouchá UDP, vícesměrového vysílání, že adresa reaguje na zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="28327-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="28327-114">Směrovač zjišťování shromažďuje odpovědi a odešle je zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="28327-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28327-115">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="28327-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="28327-116">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="28327-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="28327-117">Spuštění spustitelného souboru DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="28327-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="28327-118">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="28327-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="28327-119">Spustíte spustitelný soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="28327-119">Run the client executable.</span></span> <span data-ttu-id="28327-120">Všimněte si, že klient vyhledá službu.</span><span class="sxs-lookup"><span data-stu-id="28327-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28327-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="28327-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28327-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="28327-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28327-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="28327-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28327-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="28327-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
