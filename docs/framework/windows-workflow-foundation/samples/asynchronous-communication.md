---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e85f7efb0de1326ceb5091c305b20f34809eab57
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251583"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="4b0fb-102">Asynchronní komunikace</span><span class="sxs-lookup"><span data-stu-id="4b0fb-102">Asynchronous Communication</span></span>
<span data-ttu-id="4b0fb-103">Tato ukázka předvádí, jak je komunikace mezi dvěma různými službami Windows Workflow Foundation (WF) provádět asynchronně ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4b0fb-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4b0fb-104">Demonstrates</span></span>  
 <span data-ttu-id="4b0fb-105">Asynchronní komunikace mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4b0fb-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="4b0fb-106">Discussion</span></span>  
 <span data-ttu-id="4b0fb-107">Tato ukázka předvádí, jak komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikací se provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="4b0fb-108">Tento příklad se skládá z následujících tří projektů.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="4b0fb-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="4b0fb-109">CreditCheckService</span></span>  
 <span data-ttu-id="4b0fb-110">Tato služba přijímá skóre kredit konkrétní osoby nebo hodnotu položky, která má získat a potom rozhodne, zda tento kredit dostane osobě.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="4b0fb-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="4b0fb-111">RentalApprovalService</span></span>  
 <span data-ttu-id="4b0fb-112">Tato služba přijímá aplikace od osoby, která je potřeba zkontrolovat některé kredit.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="4b0fb-113">Tato služba komunikují asynchronně `CreditCheckService` rozhodnout, zda žádosti o kredit je platný.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="4b0fb-114">Klient</span><span class="sxs-lookup"><span data-stu-id="4b0fb-114">Client</span></span>  
 <span data-ttu-id="4b0fb-115">Klient komunikuje s synchronně `RentalApprovalService` vědět, jestli je tento kredit schválená.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b0fb-116">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="4b0fb-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4b0fb-117">Klikněte pravým tlačítkem myši **AsynchronousCommunication** řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4b0fb-118">V **společné vlastnosti**vyberte **spouštěný projekt**a vyberte **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="4b0fb-119">Přesunout **RentalApprovalService** na první místo v seznamu, za nímž následuje **CreditCheckService**následovaný **klienta**.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="4b0fb-120">Nastavte **Start** akci u všech tří projektů.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="4b0fb-121">Klikněte na tlačítko **OK**, a stiskněte klávesu F5 ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4b0fb-122">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b0fb-123">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b0fb-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b0fb-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b0fb-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4b0fb-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
