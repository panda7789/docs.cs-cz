---
title: Základní informace o využití SendParameters a ReceiveParameters aktivit
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: 8732b10f3f96ccf9ed352f9b54c60a4ee0d1664c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515395"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="4f08d-102">Základní informace o využití SendParameters a ReceiveParameters aktivit</span><span class="sxs-lookup"><span data-stu-id="4f08d-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="4f08d-103">Tento příklad ukazuje použití <xref:System.ServiceModel.Activities.SendParametersContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity.</span><span class="sxs-lookup"><span data-stu-id="4f08d-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="4f08d-104">Službu zpřístupní jednu operaci, která argument řetězce a vrátí je vstupní zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="4f08d-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="4f08d-105">Ukázka ukazuje, jak nastavit parametry pro tyto aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="4f08d-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f08d-106">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4f08d-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f08d-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4f08d-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f08d-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4f08d-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f08d-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4f08d-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="4f08d-110">Pomocí této ukázky</span><span class="sxs-lookup"><span data-stu-id="4f08d-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="4f08d-111">Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="4f08d-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="4f08d-112">Nejprve spusťte aplikaci EchoWorkflowService vygenerovaných \EchoWorkflowService\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="4f08d-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="4f08d-113">Druhý spusťte aplikaci EchoWorkflowClient vygenerovaných \EchoWorkflowClient\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="4f08d-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="4f08d-114">Klient volání operace služby Echo a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="4f08d-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="4f08d-115">Po dokončení stiskněte klávesu ENTER ukončíte klienta a pak službu.</span><span class="sxs-lookup"><span data-stu-id="4f08d-115">When complete, press ENTER to exit the client and then the service.</span></span>