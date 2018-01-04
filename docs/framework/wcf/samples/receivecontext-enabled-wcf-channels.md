---
title: "Kanály WCF povolenou třídou ReceiveContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765efb43efc0ea60ebb71bc8cdb5bd8edf973c2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="d4290-102">Kanály WCF povolenou třídou ReceiveContext</span><span class="sxs-lookup"><span data-stu-id="d4290-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="d4290-103">Tento příklad znázorňuje užitečnost <xref:System.ServiceModel.Channels.ReceiveContext>-Povolit kanály WCF.</span><span class="sxs-lookup"><span data-stu-id="d4290-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="d4290-104">Ukázka implementuje služby Vrátí součin dvou čísel pomocí NetMSMQ kanál.</span><span class="sxs-lookup"><span data-stu-id="d4290-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="d4290-105"><xref:System.ServiceModel.Channels.ReceiveContext> Třída umožňuje aplikaci rozhodnout, jestli se má přístup ke zprávě, nebo nechte ve frontě pro další zpracování, i když obsah zprávy být zkontrolovány.</span><span class="sxs-lookup"><span data-stu-id="d4290-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="d4290-106">V této ukázce klient odešle náhodných celá čísla do transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="d4290-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="d4290-107">`ProductCalculator` Služba přijímá zprávy a zkontroluje, zda obsahuje obsah zprávy, které jsou celá čísla, chcete-li zjistit, jestli je možné vypočítat produktu.</span><span class="sxs-lookup"><span data-stu-id="d4290-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="d4290-108">Pokud operace služby nepočítá produktu, zpráva se vrátit zpět do fronty a lze znovu přijímat pomocí služby naslouchá na fronty.</span><span class="sxs-lookup"><span data-stu-id="d4290-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4290-109">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d4290-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d4290-110">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="d4290-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4290-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d4290-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4290-112">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="d4290-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d4290-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="d4290-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="d4290-114">Zkontrolujte, zda je nainstalovaný Microsoft služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="d4290-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="d4290-115">Chcete-li nainstalujte službu MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d4290-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="d4290-116">V **správce serveru**, klikněte na tlačítko **funkce**.</span><span class="sxs-lookup"><span data-stu-id="d4290-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="d4290-117">V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="d4290-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="d4290-118">V okně výsledné rozbalte **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="d4290-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="d4290-119">Rozbalte položku **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="d4290-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="d4290-120">Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně) a potom klikněte na **podpora protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="d4290-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="d4290-121">Klikněte na tlačítko **Další**a potom klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="d4290-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="d4290-122">Chcete-li nainstalujte službu MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d4290-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="d4290-123">Otevřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="d4290-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="d4290-124">Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="d4290-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="d4290-125">Rozbalte položku **Server Microsoft Message Queue (MSMQ)**, rozbalte položku **jádra serveru Microsoft Message Queue (MSMQ)**a pak zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:</span><span class="sxs-lookup"><span data-stu-id="d4290-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="d4290-126">Server služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="d4290-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="d4290-127">Active Directory Domain Services integrována (pro počítače připojené k doméně)</span><span class="sxs-lookup"><span data-stu-id="d4290-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="d4290-128">Podpora protokolu HTTP služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="d4290-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="d4290-129">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="d4290-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="d4290-130">Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.</span><span class="sxs-lookup"><span data-stu-id="d4290-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="d4290-131">Ujistěte se, že [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="d4290-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="d4290-132">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="d4290-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="d4290-133">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="d4290-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="d4290-134">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="d4290-134">To run the solution, press CTRL+F5.</span></span>
