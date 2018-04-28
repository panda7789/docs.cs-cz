---
title: Asynchronní komunikaci
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9cf1cc88f2b9dda0b0f6e155a5d6a465552d6267
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="asynchronous-communication"></a><span data-ttu-id="598a3-102">Asynchronní komunikaci</span><span class="sxs-lookup"><span data-stu-id="598a3-102">Asynchronous Communication</span></span>
<span data-ttu-id="598a3-103">Tento příklad znázorňuje, jak komunikaci mezi dvěma různými službami Windows Workflow Foundation (WF) probíhá asynchronně ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="598a3-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="598a3-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="598a3-104">Demonstrates</span></span>  
 <span data-ttu-id="598a3-105">Asynchronní komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="598a3-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="598a3-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="598a3-106">Discussion</span></span>  
 <span data-ttu-id="598a3-107">Tento příklad ukazuje, jak komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikací se provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="598a3-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="598a3-108">Tato ukázka se skládá z následujících tří projektů.</span><span class="sxs-lookup"><span data-stu-id="598a3-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="598a3-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="598a3-109">CreditCheckService</span></span>  
 <span data-ttu-id="598a3-110">Tato služba přijímá skóre platební konkrétní osoby nebo hodnota položky získat a potom se rozhodne, zda je zadána se kredit osobě.</span><span class="sxs-lookup"><span data-stu-id="598a3-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="598a3-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="598a3-111">RentalApprovalService</span></span>  
 <span data-ttu-id="598a3-112">Tato služba přijímá aplikace z osoba, která je potřeba zkontrolovat některé kreditu.</span><span class="sxs-lookup"><span data-stu-id="598a3-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="598a3-113">Tato služba komunikuje asynchronně `CreditCheckService` rozhodnout, zda je aplikace platební platný.</span><span class="sxs-lookup"><span data-stu-id="598a3-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="598a3-114">Klient</span><span class="sxs-lookup"><span data-stu-id="598a3-114">Client</span></span>  
 <span data-ttu-id="598a3-115">Klient komunikuje s synchronně `RentalApprovalService` vědět, jestli je schváleno se kredit.</span><span class="sxs-lookup"><span data-stu-id="598a3-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="598a3-116">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="598a3-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="598a3-117">Klikněte pravým tlačítkem myši **AsynchronousCommunication** řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="598a3-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="598a3-118">V **společných vlastností**, vyberte **spouštěný projekt**a vyberte **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="598a3-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="598a3-119">Přesunout **RentalApprovalService** na první pozici v seznamu, následuje **CreditCheckService**, za nímž následují **klienta**.</span><span class="sxs-lookup"><span data-stu-id="598a3-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="598a3-120">Nastavte **spustit** akce na všech tří projektů.</span><span class="sxs-lookup"><span data-stu-id="598a3-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="598a3-121">Klikněte na tlačítko **OK**, a stisknutím klávesy F5 spusťte vzorku.</span><span class="sxs-lookup"><span data-stu-id="598a3-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="598a3-122">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="598a3-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="598a3-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="598a3-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="598a3-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="598a3-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="598a3-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="598a3-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
