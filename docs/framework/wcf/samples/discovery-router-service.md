---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 9c0c409eb6cf3146a198b9f4bcd6d76660f5da36
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409111"
---
# <a name="discovery-router-service"></a><span data-ttu-id="97900-102">Služba zjišťování směrovačů</span><span class="sxs-lookup"><span data-stu-id="97900-102">Discovery Router Service</span></span>
<span data-ttu-id="97900-103">Tento příklad ukazuje, jak předávat zprávy zjišťování do jiného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="97900-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="97900-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="97900-104">Demonstrates</span></span>  
 <span data-ttu-id="97900-105">Zjišťování směrování</span><span class="sxs-lookup"><span data-stu-id="97900-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="97900-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="97900-106">Discussion</span></span>  
 <span data-ttu-id="97900-107">Zjišťování směrování je užitečné pro scénáře, ve kterém hledá klienta ke službě pomocí proxy serveru a proxy serveru Nepozná takové služby, ale zná další proxy.</span><span class="sxs-lookup"><span data-stu-id="97900-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="97900-108">Tento proxy server může předat paket zjišťování od tohoto klienta na druhý server proxy.</span><span class="sxs-lookup"><span data-stu-id="97900-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="97900-109">Druhý proxy můžete vyhledat službu a vracet odpovědi na původní klienta.</span><span class="sxs-lookup"><span data-stu-id="97900-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="97900-110">V této ukázce klient odešle zprávu do komponenty směrování zjišťování.</span><span class="sxs-lookup"><span data-stu-id="97900-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="97900-111">Tato zpráva se pošle určitý koncový bod zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="97900-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="97900-112">Směrovač pak předá zprávu UDP vícesměrového vysílání koncový bod.</span><span class="sxs-lookup"><span data-stu-id="97900-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="97900-113">Průzkumné zprávy dostane k vícesměrového vysílání koncových bodů a služba naslouchá na vícesměrového vysílání UDP, že adresa reaguje na zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="97900-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="97900-114">Zjišťování směrovače odpovědi shromažďuje a odesílá zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="97900-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="97900-115">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="97900-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="97900-116">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="97900-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="97900-117">Spuštění spustitelného souboru DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="97900-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="97900-118">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="97900-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="97900-119">Spusťte klientský spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="97900-119">Run the client executable.</span></span> <span data-ttu-id="97900-120">Všimněte si, že klient vyhledá službu.</span><span class="sxs-lookup"><span data-stu-id="97900-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97900-121">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="97900-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="97900-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="97900-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="97900-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="97900-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97900-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="97900-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
