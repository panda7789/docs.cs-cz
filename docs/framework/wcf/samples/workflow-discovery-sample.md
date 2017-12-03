---
title: "Ukázka zjišťování pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba400a4476ffd2589af1d5e7d3e0ca5661102f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="1ee4f-102">Ukázka zjišťování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ee4f-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="1ee4f-103">Tento příklad znázorňuje, jak zjistitelnost služby pracovních postupů a jak vytvořit vlastní kód aktivity, která hledá pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1ee4f-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="1ee4f-104">Demonstrates</span></span>  
 <span data-ttu-id="1ee4f-105">Aktivita zjišťování najít a využití pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ee4f-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1ee4f-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="1ee4f-106">Discussion</span></span>  
 <span data-ttu-id="1ee4f-107">V první části Ukázky, se provádí zjistitelný služby pracovního postupu pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="1ee4f-108">Konfigurace lze také použít službu správně s vlastní metadata (například obory).</span><span class="sxs-lookup"><span data-stu-id="1ee4f-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="1ee4f-109">Příklad na straně klienta používá aktivitu vlastní kód, který používá k hledání zjišťování služby odpovídající konkrétní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="1ee4f-110">Kód aktivity výstupy identifikátor URI, který se později používá pomocí aktivity odeslání.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1ee4f-111">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="1ee4f-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1ee4f-112">Tato ukázka používá koncových bodů protokolu HTTP, které musí mít správnou adresu URL seznamy řízení přístupu ke spuštění (v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti).</span><span class="sxs-lookup"><span data-stu-id="1ee4f-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="1ee4f-113">Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními měli přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="1ee4f-114">Nahraďte domény a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="1ee4f-115">**netsh http přidejte adresu url urlacl = http: / / +: 8000 / uživatele domény % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="1ee4f-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1ee4f-116">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1ee4f-117">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1ee4f-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1ee4f-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ee4f-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1ee4f-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
