---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: ec4b956a28048c0c30a4eadb0473adb34334fa92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503436"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="9e3c4-102">Ukázka zjišťování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9e3c4-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="9e3c4-103">Tento příklad znázorňuje, jak zjistitelnost služby pracovních postupů a jak vytvořit vlastní kód aktivity, která hledá pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9e3c4-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="9e3c4-104">Demonstrates</span></span>  
 <span data-ttu-id="9e3c4-105">Aktivita zjišťování najít a využití pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9e3c4-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9e3c4-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="9e3c4-106">Discussion</span></span>  
 <span data-ttu-id="9e3c4-107">V první části Ukázky, se provádí zjistitelný služby pracovního postupu pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="9e3c4-108">Konfigurace lze také použít službu správně s vlastní metadata (například obory).</span><span class="sxs-lookup"><span data-stu-id="9e3c4-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="9e3c4-109">Příklad na straně klienta používá aktivitu vlastní kód, který používá k hledání zjišťování služby odpovídající konkrétní smlouvou.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="9e3c4-110">Kód aktivity výstupy identifikátor URI, který se později používá pomocí aktivity odeslání.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9e3c4-111">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9e3c4-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9e3c4-112">Tato ukázka používá koncových bodů protokolu HTTP, které musí mít správnou adresu URL seznamy řízení přístupu ke spuštění (v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti).</span><span class="sxs-lookup"><span data-stu-id="9e3c4-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="9e3c4-113">Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními měli přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="9e3c4-114">Nahraďte domény a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="9e3c4-115">**netsh http přidejte adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="9e3c4-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e3c4-116">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9e3c4-117">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9e3c4-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9e3c4-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9e3c4-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9e3c4-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
