---
title: Základní použití aktivit SendParameters a ReceiveParameters
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504005"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="ea885-102">Základní použití aktivit SendParameters a ReceiveParameters</span><span class="sxs-lookup"><span data-stu-id="ea885-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="ea885-103">Tento příklad ukazuje použití <xref:System.ServiceModel.Activities.SendParametersContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea885-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="ea885-104">Služba zpřístupňuje jedna operace, která přijímá řetězcový argument a vrátí vstupní zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="ea885-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="ea885-105">Vzorek ukazuje, jak nastavit parametry pro tyto zasílání zpráv aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea885-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ea885-106">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ea885-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ea885-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ea885-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ea885-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ea885-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea885-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ea885-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="ea885-110">Pomocí této ukázky</span><span class="sxs-lookup"><span data-stu-id="ea885-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="ea885-111">Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="ea885-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="ea885-112">Nejprve spusťte aplikaci EchoWorkflowService vygenerované v \EchoWorkflowService\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="ea885-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="ea885-113">Za druhé spusťte aplikaci EchoWorkflowClient vygenerované v \EchoWorkflowClient\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="ea885-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="ea885-114">Klient volá operace služby Echo a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="ea885-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="ea885-115">Jakmile budete hotovi, stisknutím klávesy ENTER ukončete klienta a pak službu.</span><span class="sxs-lookup"><span data-stu-id="ea885-115">When complete, press ENTER to exit the client and then the service.</span></span>