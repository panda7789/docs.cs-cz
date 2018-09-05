---
title: Korelovaná Kalkulačka
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517310"
---
# <a name="correlated-calculator"></a><span data-ttu-id="91ced-102">Korelovaná Kalkulačka</span><span class="sxs-lookup"><span data-stu-id="91ced-102">Correlated Calculator</span></span>
<span data-ttu-id="91ced-103">Tento příklad ukazuje, jak pomocí aktivit zasílání zpráv (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>) v návrháři se korelace na základě obsahu na základě parametru ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="91ced-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="91ced-104">V tomto scénáři jsou operace kalkulačky v paralelní doprovodný.</span><span class="sxs-lookup"><span data-stu-id="91ced-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="91ced-105">Instance a korelaci (na základě `CalculatorId`) se vytvoří, když je první zpráva odeslána do pracovního postupu a následné zprávy se stejnou `CalculatorId` se odesílají do této instance, dokud volat operaci resetování.</span><span class="sxs-lookup"><span data-stu-id="91ced-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="91ced-106">Klient je implementovaný jako aplikaci WPF, která používá proxy server založený na kódu klienta ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="91ced-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="91ced-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="91ced-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="91ced-108">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] v zvýšenou úroveň oprávnění, otevřete soubor řešení For.sln.</span><span class="sxs-lookup"><span data-stu-id="91ced-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="91ced-109">Přejděte do složky, která obsahuje [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91ced-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="91ced-110">Klikněte pravým tlačítkem na Devenv.exe a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="91ced-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="91ced-111">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="91ced-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="91ced-112">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="91ced-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="91ced-113">Chcete-li spustit projekt služby, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="91ced-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="91ced-114">Jakmile služba je připravená a naslouchá pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte jej.</span><span class="sxs-lookup"><span data-stu-id="91ced-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91ced-115">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="91ced-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="91ced-116">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="91ced-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="91ced-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="91ced-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91ced-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="91ced-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`