---
title: "Pouze služba základní XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06a302b13db3b82dabb43989ac272df0d9aac008
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="89aff-102">Pouze služba základní XAML</span><span class="sxs-lookup"><span data-stu-id="89aff-102">Basic XAML only Service</span></span>
<span data-ttu-id="89aff-103">Tento příklad znázorňuje způsob vytvoření služby pouze XAML.</span><span class="sxs-lookup"><span data-stu-id="89aff-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="89aff-104">Tento scénář je služba diagnostiky pro problémy související s Auto.</span><span class="sxs-lookup"><span data-stu-id="89aff-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="89aff-105">Služba se implementuje jako pracovní postup, který klient zeptá na několik otázek a diagnostikovat problém.</span><span class="sxs-lookup"><span data-stu-id="89aff-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="89aff-106">Existují dva typy službu lze diagnostikovat problémy (car nezačíná ani klimatizace nepracuje).</span><span class="sxs-lookup"><span data-stu-id="89aff-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="89aff-107">Pracovní postup používá šablonu požadavek nebo odpověď z Návrháře ke zveřejnění tři operací jednoduché služby.</span><span class="sxs-lookup"><span data-stu-id="89aff-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="89aff-108">Služba je hostovaná ve službě IIS tak, že vytvoříte virtuální adresář ve službě IIS a kopírování service1.xamlx a souborů Web.config do virtuálního adresáře, žádné zkompilovaný kód je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="89aff-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="89aff-109">Ve výchozím nastavení tato ukázka automaticky zkopíruje potřebné soubory do virtuální adresář vytvořen, pokud budete postupovat podle pokynů instalačního programu pro ukázky WCF a WF: [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) při sestavení v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="89aff-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="89aff-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="89aff-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="89aff-111">Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="89aff-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="89aff-112">Spusťte klientskou aplikaci vygenerovaných \Client\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="89aff-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="89aff-113">Aplikace vytiskne možnosti, vybere možnost.</span><span class="sxs-lookup"><span data-stu-id="89aff-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="89aff-114">Aplikace se pak požádá otázky, odpovědi je Ano nebo ne (pomocí klíče A/N).</span><span class="sxs-lookup"><span data-stu-id="89aff-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="89aff-115">Pokud se provádí služba diagnostice problémů, vytiskne aplikace diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="89aff-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="89aff-116">Aplikace přejde zpět na možnosti.</span><span class="sxs-lookup"><span data-stu-id="89aff-116">The application goes back to the options.</span></span> <span data-ttu-id="89aff-117">Můžete diagnostikovat jiný problém nebo ukončit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89aff-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89aff-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="89aff-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="89aff-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="89aff-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="89aff-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="89aff-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89aff-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="89aff-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`