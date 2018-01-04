---
title: "Načtení z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28f5f4a57f8fd6ee8b739b38735d41a118abc0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="load-from-xaml"></a><span data-ttu-id="51043-102">Načtení z XAML</span><span class="sxs-lookup"><span data-stu-id="51043-102">Load From XAML</span></span>
<span data-ttu-id="51043-103">Tato ukázka ukazuje, jak se dynamicky načíst postupu v XML bez nutnosti spustit nástroj XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="51043-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="51043-104">Místo toho ukázka volá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="51043-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="51043-105">Ukázka je [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] klientskou aplikaci, která načte pomocí pracovních postupů XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a spustí je.</span><span class="sxs-lookup"><span data-stu-id="51043-105">The sample is a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="51043-106">Po jejich byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třída, <xref:System.Activities.DynamicActivity%601> se vrátí, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="51043-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="51043-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="51043-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="51043-108">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="51043-108">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LoadFromXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="51043-109">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="51043-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="51043-110">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="51043-110">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51043-111">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="51043-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51043-112">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="51043-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="51043-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="51043-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51043-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="51043-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`