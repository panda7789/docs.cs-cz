---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183731"
---
# <a name="discovery-router-service"></a><span data-ttu-id="32504-102">Služba zjišťování směrovačů</span><span class="sxs-lookup"><span data-stu-id="32504-102">Discovery Router Service</span></span>
<span data-ttu-id="32504-103">Tato ukázka ukazuje, jak předat zprávy zjišťování do jiného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="32504-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="32504-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="32504-104">Demonstrates</span></span>  
 <span data-ttu-id="32504-105">Směrování zjišťování</span><span class="sxs-lookup"><span data-stu-id="32504-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="32504-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="32504-106">Discussion</span></span>  
 <span data-ttu-id="32504-107">Směrování zjišťování je užitečné ve scénáři, ve kterém klient hledá službu pomocí proxy serveru a proxy server o takové službě neví, ale ví o jiném serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="32504-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="32504-108">Tento proxy server může předat paket zjišťování z tohoto klienta druhému serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="32504-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="32504-109">Druhý proxy server může vyhledat službu a vrátit odpovědi původnímu klientovi.</span><span class="sxs-lookup"><span data-stu-id="32504-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="32504-110">V této ukázce klient odešle zprávu součásti směrování zjišťování.</span><span class="sxs-lookup"><span data-stu-id="32504-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="32504-111">Tato zpráva je odeslána do určitého koncového bodu na směrovači zjišťování.</span><span class="sxs-lookup"><span data-stu-id="32504-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="32504-112">Směrovač pak předá zprávu koncovému bodu vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="32504-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="32504-113">Zpráva sondy zhasne do koncového bodu vícesměrového vysílání a služba naslouchající na adrese vícesměrového vysílání UDP odpoví na tento směrovač zjišťování.</span><span class="sxs-lookup"><span data-stu-id="32504-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="32504-114">Zjišťování směrovač shromažďuje odpovědi a odešle je zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="32504-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="32504-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="32504-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="32504-116">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="32504-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="32504-117">Spusťte spustitelný soubor DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="32504-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="32504-118">Spusťte spustitelný soubor služby z adresáře sestavení.</span><span class="sxs-lookup"><span data-stu-id="32504-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="32504-119">Spusťte spustitelný soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="32504-119">Run the client executable.</span></span> <span data-ttu-id="32504-120">Všimněte si, že klient vyhledá službu.</span><span class="sxs-lookup"><span data-stu-id="32504-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="32504-121">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="32504-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32504-122">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="32504-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="32504-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="32504-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32504-124">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="32504-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
