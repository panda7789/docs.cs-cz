---
title: Odeslání a zpracování chyb
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516123"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="3827b-102">Odeslání a zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="3827b-102">Sending and Handling Faults</span></span>
<span data-ttu-id="3827b-103">Tento příklad znázorňuje způsob použití <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity pro odesílání a přijímání očekávané a neočekávané chyby zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3827b-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="3827b-104">V tomto scénáři první klient v požadavku má za následek očekávané selhání, který byl zahrnut v jeho <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="3827b-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="3827b-105">Další požadavky několik klientů za následek před posledním neproběhne přijetí neočekávané chyby.</span><span class="sxs-lookup"><span data-stu-id="3827b-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="3827b-106">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="3827b-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="3827b-107">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="3827b-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="3827b-108">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="3827b-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="3827b-109">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3827b-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="3827b-110">Spusťte projekt služby.</span><span class="sxs-lookup"><span data-stu-id="3827b-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="3827b-111">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultService` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="3827b-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="3827b-112">Stisknutím klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="3827b-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="3827b-113">Otevřete jinou kopii [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="3827b-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="3827b-114">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="3827b-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="3827b-115">Spuštění klientského projektu.</span><span class="sxs-lookup"><span data-stu-id="3827b-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="3827b-116">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultClient` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="3827b-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="3827b-117">Stisknutím klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="3827b-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3827b-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3827b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3827b-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3827b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3827b-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3827b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3827b-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3827b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`