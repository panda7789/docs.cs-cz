---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 9434c26fb12b73ea4f1c185658b03cb95a3a2310
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039832"
---
# <a name="discovery-router-service"></a><span data-ttu-id="ede7a-102">Služba zjišťování směrovačů</span><span class="sxs-lookup"><span data-stu-id="ede7a-102">Discovery Router Service</span></span>
<span data-ttu-id="ede7a-103">Tato ukázka předvádí, jak předávané zprávy zjišťování do jiného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ede7a-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ede7a-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="ede7a-104">Demonstrates</span></span>  
 <span data-ttu-id="ede7a-105">Směrování zjišťování</span><span class="sxs-lookup"><span data-stu-id="ede7a-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ede7a-106">Účely</span><span class="sxs-lookup"><span data-stu-id="ede7a-106">Discussion</span></span>  
 <span data-ttu-id="ede7a-107">Směrování zjišťování je užitečné ve scénáři, ve kterém klient hledá službu pomocí proxy serveru a proxy server tuto službu neví, ale ví o jiném proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="ede7a-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="ede7a-108">Tento proxy server může přeposláním paketu zjišťování od tohoto klienta k druhému proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="ede7a-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="ede7a-109">Druhý proxy server může hledat službu a vracet odpovědi původnímu klientovi.</span><span class="sxs-lookup"><span data-stu-id="ede7a-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="ede7a-110">V této ukázce klient pošle zprávu na součást směrování zjišťování.</span><span class="sxs-lookup"><span data-stu-id="ede7a-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="ede7a-111">Tato zpráva se odešle do konkrétního koncového bodu ve směrovači zjišťování.</span><span class="sxs-lookup"><span data-stu-id="ede7a-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="ede7a-112">Směrovač pak přepošle zprávu na koncový bod vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="ede7a-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="ede7a-113">Zpráva testu se překročí na koncový bod vícesměrového vysílání a služba, která naslouchá na adrese vícesměrového vysílání UDP, reaguje na tento směrovač zjišťování.</span><span class="sxs-lookup"><span data-stu-id="ede7a-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="ede7a-114">Směrovač zjišťování shromáždí odpovědi a pošle je zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="ede7a-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ede7a-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ede7a-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ede7a-116">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="ede7a-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="ede7a-117">Spusťte spustitelný soubor DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="ede7a-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="ede7a-118">Spusťte spustitelný soubor služby z adresáře buildu.</span><span class="sxs-lookup"><span data-stu-id="ede7a-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="ede7a-119">Spusťte klientský spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="ede7a-119">Run the client executable.</span></span> <span data-ttu-id="ede7a-120">Všimněte si, že klient vyhledává službu.</span><span class="sxs-lookup"><span data-stu-id="ede7a-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ede7a-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ede7a-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ede7a-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ede7a-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ede7a-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ede7a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ede7a-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ede7a-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
