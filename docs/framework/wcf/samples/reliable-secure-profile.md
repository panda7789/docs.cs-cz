---
title: "Řešení ReliableSecureProfile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6b73565409e26456ad09067066455ef2459b2e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-secure-profile"></a><span data-ttu-id="559f9-102">Řešení ReliableSecureProfile</span><span class="sxs-lookup"><span data-stu-id="559f9-102">Reliable Secure Profile</span></span>
<span data-ttu-id="559f9-103">Tento příklad ukazuje, jak vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [spolehlivé profil zabezpečení](http://go.microsoft.com/fwlink/?LinkId=178140) (konfigurace).</span><span class="sxs-lookup"><span data-stu-id="559f9-103">This sample demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP).</span></span> <span data-ttu-id="559f9-104">Tento příklad znázorňuje implementaci [vytvořit připojení](http://go.microsoft.com/fwlink/?LinkId=178141) kanál, který může být složené, společně s spolehlivé zasílání zpráv a volitelně zabezpečený kanál vytvořit spolehlivá zabezpečené vazby podle specifikace konfigurace.</span><span class="sxs-lookup"><span data-stu-id="559f9-104">This sample demonstrates the implementation of a [Make Connection](http://go.microsoft.com/fwlink/?LinkId=178141) channel which can be composed together with Reliable Messaging and optionally a secure channel to create a Reliable Secure Binding based on the RSP specification.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="559f9-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="559f9-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="559f9-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="559f9-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="559f9-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="559f9-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="559f9-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="559f9-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a><span data-ttu-id="559f9-109">Diskusní</span><span class="sxs-lookup"><span data-stu-id="559f9-109">Discussion</span></span>  
 <span data-ttu-id="559f9-110">Tento příklad znázorňuje scénáři exchange spolehlivé asynchronní obousměrný zprávu.</span><span class="sxs-lookup"><span data-stu-id="559f9-110">This sample demonstrates a reliable asynchronous two-way message exchange scenario.</span></span> <span data-ttu-id="559f9-111">Služba má duplexního kontraktu a implementuje kontrakt duplexní zpětné volání klienta.</span><span class="sxs-lookup"><span data-stu-id="559f9-111">The service has a duplex contract and the client implements the duplex callback contract.</span></span> <span data-ttu-id="559f9-112">Klient inicializuje požadavek na službu, pro kterou je očekáván odpověď na samostatné připojení.</span><span class="sxs-lookup"><span data-stu-id="559f9-112">The client initiates a request to a service, for which a response is expected on a separate connection.</span></span> <span data-ttu-id="559f9-113">Spolehlivě je odeslána zpráva požadavku.</span><span class="sxs-lookup"><span data-stu-id="559f9-113">The request message is sent reliably.</span></span> <span data-ttu-id="559f9-114">Klient nechce otevřete koncový bod naslouchání v jeho koncem.</span><span class="sxs-lookup"><span data-stu-id="559f9-114">The client does not want to open a listening endpoint at its end.</span></span> <span data-ttu-id="559f9-115">Proto dotazuje službu s vytvořit připojení žádosti o službu má být zaslán zpět odpověď na používající back channel tohoto požadavku vytvořit připojení.</span><span class="sxs-lookup"><span data-stu-id="559f9-115">Thus, it polls the service with ‘Make Connection’ requests for the service to send back the response on the back channel of this ‘Make Connection’ request.</span></span> <span data-ttu-id="559f9-116">Tento příklad ukazuje, jak tak, aby měl zabezpečené spolehlivé duplexní komunikace přes protokol HTTP bez klienta vystavení naslouchání koncového bodu (a vytváření výjimku brány firewall).</span><span class="sxs-lookup"><span data-stu-id="559f9-116">This sample demonstrates how to have secure reliable duplex communication over HTTP without the client exposing a listening endpoint (and creating a firewall exception).</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="559f9-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="559f9-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="559f9-118">Otevřete **ReliableSecureProfile** řešení.</span><span class="sxs-lookup"><span data-stu-id="559f9-118">Open the **ReliableSecureProfile** solution.</span></span>  
  
2.  <span data-ttu-id="559f9-119">Klikněte pravým tlačítkem **služby** projektu v **Průzkumníku řešení**, vyberte **ladění**, **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="559f9-119">Right click the **Service** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="559f9-120">Tím se spustí až hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="559f9-120">This starts up the service host.</span></span>  
  
3.  <span data-ttu-id="559f9-121">Klikněte pravým tlačítkem **klienta** projektu v **Průzkumníku řešení**, vyberte **ladění**, **spustit novou instanci** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="559f9-121">Right click the **Client** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="559f9-122">To spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="559f9-122">This starts up the client.</span></span>  
  
4.  <span data-ttu-id="559f9-123">Zadejte do libovolného řetězce v řádku v okně konzoly klienta a stiskněte ENTER. Vstupní řetězec tím se odešle do služby, která vypočítá hodnotu hash tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="559f9-123">Type in any string in the prompt on the client console window and click ENTER.This sends the input string to the service, which computes a hash of this string.</span></span>  
  
5.  <span data-ttu-id="559f9-124">Zobrazení výsledek na klienta windows, když služba zpětným voláním operace zpětného duplexní kontrakt zobrazíte výsledek na okna konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="559f9-124">View the result on the client windows when the service calls back the duplex callback contract operation to display the result on the client console window.</span></span> <span data-ttu-id="559f9-125">Na službu, kterou chcete simulovat dlouhotrvající operace zpracování dat je úmyslné zpoždění.</span><span class="sxs-lookup"><span data-stu-id="559f9-125">There is an intentional delay on the service to simulate a long running operation of processing the data.</span></span>  
  
6.  <span data-ttu-id="559f9-126">Monitorování provoz HTTP (podle online sítě monitorování nástroje, například sledování sítě, Fiddler a tak dále) ukázáno, že pořadí pro komunikaci mezi klientem a službu podle stanovených spolehlivé profil zabezpečení a jak klienta dotazuje službu s požadavky vytvořit připojení.</span><span class="sxs-lookup"><span data-stu-id="559f9-126">Monitoring the HTTP traffic (by any of the online network monitoring tools like Network Monitor, Fiddler and so on) shows that a sequence for communication is established between the client and the service as laid down by the Reliable Secure Profile, and how the client polls the service with ‘Make Connection’ requests.</span></span> <span data-ttu-id="559f9-127">Když služba získá připravené má být zaslán zpět zpracování odpovědi, používá používající back channel poslední žádosti vytvořit připojení má být zaslán zpět výsledky.</span><span class="sxs-lookup"><span data-stu-id="559f9-127">When the service gets ready to send back the processed response, it uses the back channel of the last ‘Make Connection’ request to send back the results.</span></span>  
  
7.  <span data-ttu-id="559f9-128">V okně konzoly služby službu zavřete stisknutím klávesy ENTER.</span><span class="sxs-lookup"><span data-stu-id="559f9-128">Press ENTER on the service console window to close the service.</span></span> <span data-ttu-id="559f9-129">Stiskněte klávesu ENTER na okna konzoly klienta zavřít klienta.</span><span class="sxs-lookup"><span data-stu-id="559f9-129">Press ENTER on the client console window to close the client.</span></span>
