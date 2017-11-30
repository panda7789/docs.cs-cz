---
title: "Odeslání a zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 70693af8582de084894275c832e451d7f0fee794
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="f1fee-102">Odeslání a zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="f1fee-102">Sending and Handling Faults</span></span>
<span data-ttu-id="f1fee-103">Tento příklad znázorňuje způsob použití <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity pro odesílání a přijímání očekávané a neočekávané chyby zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f1fee-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="f1fee-104">V tomto scénáři první klient v požadavku má za následek očekávané selhání, který byl zahrnut v jeho <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="f1fee-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="f1fee-105">Další požadavky několik klientů za následek před posledním neproběhne přijetí neočekávané chyby.</span><span class="sxs-lookup"><span data-stu-id="f1fee-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="f1fee-106">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="f1fee-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="f1fee-107">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="f1fee-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="f1fee-108">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="f1fee-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="f1fee-109">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f1fee-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="f1fee-110">Spusťte projekt služby.</span><span class="sxs-lookup"><span data-stu-id="f1fee-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="f1fee-111">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultService` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f1fee-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="f1fee-112">Stisknutím klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f1fee-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="f1fee-113">Otevřete jinou kopii [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="f1fee-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="f1fee-114">Otevřete soubor řešení Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="f1fee-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="f1fee-115">Spuštění klientského projektu.</span><span class="sxs-lookup"><span data-stu-id="f1fee-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="f1fee-116">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultClient` projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f1fee-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="f1fee-117">Stisknutím klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f1fee-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1fee-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f1fee-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1fee-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f1fee-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1fee-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f1fee-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1fee-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f1fee-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`