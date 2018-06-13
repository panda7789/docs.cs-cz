---
title: Korelační kalkulačky
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514138"
---
# <a name="correlated-calculator"></a><span data-ttu-id="07b6c-102">Korelační kalkulačky</span><span class="sxs-lookup"><span data-stu-id="07b6c-102">Correlated Calculator</span></span>
<span data-ttu-id="07b6c-103">Tento příklad znázorňuje způsob použití zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>) v návrháři se korelace na základě obsahu na základě parametru ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="07b6c-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="07b6c-104">V tomto scénáři jsou operace kalkulačky v paralelní convoy.</span><span class="sxs-lookup"><span data-stu-id="07b6c-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="07b6c-105">Instance a existuje korelace (na základě `CalculatorId`) se vytvoří, když je první zpráva odeslána do pracovního postupu a dalších zpráv se stejným `CalculatorId` se odesílají do této instance, dokud operace resetování, se nazývá.</span><span class="sxs-lookup"><span data-stu-id="07b6c-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="07b6c-106">Klient je implementovaný jako WPF aplikace, která používá proxy server založené na kódu klienta ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="07b6c-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="07b6c-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="07b6c-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="07b6c-108">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] v zvýšenými oprávněními, otevřete soubor řešení For.sln.</span><span class="sxs-lookup"><span data-stu-id="07b6c-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="07b6c-109">Přejděte do složky, která obsahuje [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07b6c-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="07b6c-110">Klikněte pravým tlačítkem na Devenv.exe a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="07b6c-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="07b6c-111">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="07b6c-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="07b6c-112">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="07b6c-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="07b6c-113">Chcete-li spustit projekt služby, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="07b6c-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="07b6c-114">Jakmile služba je připravena a naslouchání pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="07b6c-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07b6c-115">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="07b6c-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07b6c-116">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="07b6c-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07b6c-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="07b6c-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07b6c-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="07b6c-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`