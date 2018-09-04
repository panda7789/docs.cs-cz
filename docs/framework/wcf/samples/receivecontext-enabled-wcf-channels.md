---
title: Kanály WCF povolenou třídou ReceiveContext
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515927"
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="31e38-102">Kanály WCF povolenou třídou ReceiveContext</span><span class="sxs-lookup"><span data-stu-id="31e38-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="31e38-103">V této ukázce užitečnost <xref:System.ServiceModel.Channels.ReceiveContext>-povoleno kanály WCF.</span><span class="sxs-lookup"><span data-stu-id="31e38-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="31e38-104">Ukázka implementuje službu, která vrátí součin dvou čísel pomocí NetMSMQ kanálu.</span><span class="sxs-lookup"><span data-stu-id="31e38-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="31e38-105"><xref:System.ServiceModel.Channels.ReceiveContext> Třída umožňuje aplikaci se rozhodnout, jestli se má přístup ke zprávě, nebo nechat ji ve frontě pro další zpracování, i když byly podrobeny obsah zprávy.</span><span class="sxs-lookup"><span data-stu-id="31e38-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="31e38-106">V této ukázce klient odešle náhodné celých čísel na transakční frontu.</span><span class="sxs-lookup"><span data-stu-id="31e38-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="31e38-107">`ProductCalculator` Služba přijímá zprávy a zkontroluje obsah zprávy, které jsou celá čísla, chcete-li zjistit, zda lze vypočítat produktu.</span><span class="sxs-lookup"><span data-stu-id="31e38-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="31e38-108">Pokud operace služby nepočítá produktu, zpráva se znovu zařadí do fronty a lze znovu přijímat pomocí služby naslouchání ve frontě.</span><span class="sxs-lookup"><span data-stu-id="31e38-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31e38-109">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="31e38-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="31e38-110">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="31e38-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31e38-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="31e38-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31e38-112">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="31e38-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="31e38-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="31e38-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="31e38-114">Ujistěte se, že je nainstalovaný Microsoft Message Queuing (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="31e38-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="31e38-115">Chcete-li nainstalovat služby MSMQ v [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="31e38-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="31e38-116">V **správce serveru**, klikněte na tlačítko **funkce**.</span><span class="sxs-lookup"><span data-stu-id="31e38-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="31e38-117">V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="31e38-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="31e38-118">V okně výsledný rozbalte **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="31e38-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="31e38-119">Rozbalte **služba Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="31e38-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="31e38-120">Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně) a potom klikněte na tlačítko **podpora protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="31e38-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="31e38-121">Klikněte na tlačítko **Další**a potom klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="31e38-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="31e38-122">Chcete-li nainstalovat služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="31e38-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="31e38-123">Otevřít **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="31e38-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="31e38-124">Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.</span><span class="sxs-lookup"><span data-stu-id="31e38-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="31e38-125">Rozbalte **Server Microsoft Message Queue (MSMQ)**, rozbalte **jádra serveru Microsoft Message Queue (MSMQ)** a poté zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:</span><span class="sxs-lookup"><span data-stu-id="31e38-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="31e38-126">Server služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="31e38-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="31e38-127">MSMQ domény služby integrace služby Active Directory (pro počítače připojené k doméně)</span><span class="sxs-lookup"><span data-stu-id="31e38-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="31e38-128">Podpora protokolu HTTP služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="31e38-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="31e38-129">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="31e38-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="31e38-130">Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.</span><span class="sxs-lookup"><span data-stu-id="31e38-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="31e38-131">Ujistěte se, že [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="31e38-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="31e38-132">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="31e38-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="31e38-133">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="31e38-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="31e38-134">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="31e38-134">To run the solution, press CTRL+F5.</span></span>
