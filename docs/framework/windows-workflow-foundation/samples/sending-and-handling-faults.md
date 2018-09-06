---
title: Odesílání a zpracování chyb
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800992"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="81589-102">Odesílání a zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="81589-102">Sending and Handling Faults</span></span>
<span data-ttu-id="81589-103">Tato ukázka předvádí, jak používat <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> zasílání zpráv aktivity pro odesílání a přijímání očekávaným způsobem a neočekávané chyby.</span><span class="sxs-lookup"><span data-stu-id="81589-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="81589-104">V tomto scénáři první klient vyžádat výsledky v očekávané chybu, která obsahuje její <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="81589-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="81589-105">Další několik požadavků klientů za následek příjem neočekávané chyby, před posledním neproběhne.</span><span class="sxs-lookup"><span data-stu-id="81589-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="81589-106">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="81589-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="81589-107">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="81589-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="81589-108">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="81589-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="81589-109">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="81589-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="81589-110">Spusťte projekt služby.</span><span class="sxs-lookup"><span data-stu-id="81589-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="81589-111">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `FaultService` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="81589-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="81589-112">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="81589-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="81589-113">Otevřete jinou kopii [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="81589-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="81589-114">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="81589-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="81589-115">Spuštění klientského projektu.</span><span class="sxs-lookup"><span data-stu-id="81589-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="81589-116">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `FaultClient` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="81589-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="81589-117">Stisknutím kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="81589-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81589-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="81589-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81589-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="81589-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81589-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="81589-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81589-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="81589-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`