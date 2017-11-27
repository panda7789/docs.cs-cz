---
title: "Korelace na základě obsahu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0490dcc854a6686c69ebc480df42e6086d1fdc52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="56a58-102">Korelace na základě obsahu</span><span class="sxs-lookup"><span data-stu-id="56a58-102">Content-Based Correlation</span></span>
<span data-ttu-id="56a58-103">Tento příklad ukazuje, jak aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>) lze použít s více na základě obsahu correlations.and korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="56a58-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="56a58-104">V tomto scénáři korelace první inicializaci podle ID nákupní objednávky, a dále jiné korelace se později podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="56a58-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="56a58-105">Ukazuje to, jak <xref:System.ServiceModel.Activities.Receive> aktivity můžete postupovat podle existujících korelace i inicializovat nové korelace na základě stejné příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="56a58-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="56a58-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="56a58-106">Demonstrates</span></span>  
 <span data-ttu-id="56a58-107">Aktivity zasílání zpráv a korelace na základě obsahu</span><span class="sxs-lookup"><span data-stu-id="56a58-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="56a58-108">Diskusní</span><span class="sxs-lookup"><span data-stu-id="56a58-108">Discussion</span></span>  
 <span data-ttu-id="56a58-109">Tento příklad ukazuje, jak používat více na základě obsahu korelací.</span><span class="sxs-lookup"><span data-stu-id="56a58-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="56a58-110">V tomto scénáři korelace první inicializaci podle ID nákupní objednávky, a dále jiné korelace se později podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="56a58-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="56a58-111">Korelací jsou kaskádové pomocí <xref:System.ServiceModel.Activities.Receive> aktivity, která odpovídá existující korelace (PurchaseOrderId) i inicializuje nový korelace (CustomerId) podle stejné příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="56a58-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="56a58-112">K tomu <xref:System.ServiceModel.Activities.Receive> používá aktivitu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> a <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="56a58-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="56a58-113">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="56a58-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="56a58-114">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="56a58-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="56a58-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CascadingCorrelation.sln.</span><span class="sxs-lookup"><span data-stu-id="56a58-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="56a58-116">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="56a58-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="56a58-117">Pokud chcete spustit serveru, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="56a58-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="56a58-118">Jakmile služba je připravena a naslouchání pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="56a58-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56a58-119">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="56a58-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56a58-120">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="56a58-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="56a58-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="56a58-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56a58-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="56a58-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="56a58-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="56a58-123">See Also</span></span>
