---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142873"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="8d0bf-102">Asynchronní komunikace</span><span class="sxs-lookup"><span data-stu-id="8d0bf-102">Asynchronous Communication</span></span>
<span data-ttu-id="8d0bf-103">Tato ukázka ukazuje, jak se ve výchozím nastavení provádí komunikace mezi dvěma různými službami Nadace pracovních postupů systému Windows (WF).</span><span class="sxs-lookup"><span data-stu-id="8d0bf-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8d0bf-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="8d0bf-104">Demonstrates</span></span>  
 <span data-ttu-id="8d0bf-105">Asynchronní komunikace [!INCLUDE[wf1](../../../../includes/wf1-md.md)] mezi službami.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8d0bf-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="8d0bf-106">Discussion</span></span>  
 <span data-ttu-id="8d0bf-107">Tato ukázka ukazuje, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] jak se komunikace mezi aplikacemi provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="8d0bf-108">Tento příklad se skládá z následujících tří projektů.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="8d0bf-109">Služba CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="8d0bf-109">CreditCheckService</span></span>  
 <span data-ttu-id="8d0bf-110">Tato služba obdrží kreditní skóre určité osoby nebo hodnotu položky, kterou chcete získat, a poté rozhodne, zda je úvěr dané osobě poskytnut.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="8d0bf-111">Služba RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="8d0bf-111">RentalApprovalService</span></span>  
 <span data-ttu-id="8d0bf-112">Tato služba obdrží žádost od osoby, která potřebuje nějaký kredit.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="8d0bf-113">Tato služba komunikuje asynchronně s `CreditCheckService` rozhodnout, zda je platná aplikace úvěru.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="8d0bf-114">Klient</span><span class="sxs-lookup"><span data-stu-id="8d0bf-114">Client</span></span>  
 <span data-ttu-id="8d0bf-115">Klient synchronně komunikuje s tím, `RentalApprovalService` zda je úvěr schválen.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d0bf-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8d0bf-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8d0bf-117">Klepněte pravým tlačítkem myši na řešení **AsynchronousCommunication** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="8d0bf-118">V **pole Common Properties**vyberte možnost Projekt po **spuštění**a **vyberte možnost Více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="8d0bf-119">Přesuňte **RentalApprovalService** na první pozici v seznamu, následovanou **CreditCheckService**, následovanou **Klientem**.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="8d0bf-120">Nastavte akci **Zahájení** u všech tří projektů.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="8d0bf-121">Klepněte na tlačítko **OK**a spusťte ukázku stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8d0bf-122">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d0bf-123">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8d0bf-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d0bf-125">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8d0bf-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
