---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: b5cf788ce4587dacb5a7642e25cb1b5b1e6f3e3c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044362"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="5badf-102">Asynchronní komunikace</span><span class="sxs-lookup"><span data-stu-id="5badf-102">Asynchronous Communication</span></span>
<span data-ttu-id="5badf-103">Tato ukázka předvádí, jak je komunikace mezi dvěma různými programovací model Windows Workflow Foundation (WF) ve výchozím nastavení prováděna asynchronně.</span><span class="sxs-lookup"><span data-stu-id="5badf-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5badf-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="5badf-104">Demonstrates</span></span>  
 <span data-ttu-id="5badf-105">Asynchronní komunikace mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] službami.</span><span class="sxs-lookup"><span data-stu-id="5badf-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5badf-106">Účely</span><span class="sxs-lookup"><span data-stu-id="5badf-106">Discussion</span></span>  
 <span data-ttu-id="5badf-107">V této ukázce se dozvíte, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] jak je komunikace mezi aplikacemi prováděna asynchronně pomocí aktivit zasílání zpráv, které poskytuje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5badf-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="5badf-108">Tato ukázka se skládá z následujících tří projektů.</span><span class="sxs-lookup"><span data-stu-id="5badf-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="5badf-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="5badf-109">CreditCheckService</span></span>  
 <span data-ttu-id="5badf-110">Tato služba obdrží kreditní skóre konkrétní osoby nebo hodnotu položky, která má být získána, a pak rozhodne, zda je daný kredit dán osobě.</span><span class="sxs-lookup"><span data-stu-id="5badf-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="5badf-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="5badf-111">RentalApprovalService</span></span>  
 <span data-ttu-id="5badf-112">Tato služba obdrží aplikaci od osoby, která je v potřebě nějakého kreditu.</span><span class="sxs-lookup"><span data-stu-id="5badf-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="5badf-113">Tato služba komunikuje asynchronně s nástrojem `CreditCheckService` k rozhodnutí, zda je aplikace pro kredit platná.</span><span class="sxs-lookup"><span data-stu-id="5badf-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="5badf-114">Klient</span><span class="sxs-lookup"><span data-stu-id="5badf-114">Client</span></span>  
 <span data-ttu-id="5badf-115">Klient komunikuje synchronně s nástrojem `RentalApprovalService` , aby bylo možné zjistit, zda je kredit schválen.</span><span class="sxs-lookup"><span data-stu-id="5badf-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5badf-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5badf-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5badf-117">Klikněte pravým tlačítkem na řešení **AsynchronousCommunication** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5badf-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="5badf-118">V možnosti **společné vlastnosti**vyberte možnost **projekt po spuštění**a vyberte možnost **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="5badf-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="5badf-119">Přesuňte **RentalApprovalService** na první pozici v seznamu, za kterou následuje **CreditCheckService**a pak na **klienta**.</span><span class="sxs-lookup"><span data-stu-id="5badf-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="5badf-120">Nastavte akci **spuštění** na všech třech projektech.</span><span class="sxs-lookup"><span data-stu-id="5badf-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="5badf-121">Klikněte na **OK**a stisknutím klávesy F5 spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="5badf-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5badf-122">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5badf-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5badf-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5badf-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5badf-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="5badf-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5badf-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5badf-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
