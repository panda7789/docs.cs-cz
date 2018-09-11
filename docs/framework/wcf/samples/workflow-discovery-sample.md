---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367779"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="d22b9-102">Ukázka zjišťování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d22b9-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="d22b9-103">Tato ukázka předvádí, jak zjistitelnost služby pracovního postupu a jak si můžete vytvořit vlastní kód aktivitou, která hledá konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="d22b9-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d22b9-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="d22b9-104">Demonstrates</span></span>  
 <span data-ttu-id="d22b9-105">Zjišťování najít aktivitu a využití pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d22b9-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d22b9-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="d22b9-106">Discussion</span></span>  
 <span data-ttu-id="d22b9-107">V první části Ukázky tvoří zjistitelné služby pracovního postupu pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d22b9-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="d22b9-108">Konfigurace lze také použít službu odpovídajícím způsobem s vlastní metadata (například obory).</span><span class="sxs-lookup"><span data-stu-id="d22b9-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="d22b9-109">Ukázka používá na klientovi, kód vlastní aktivitu, která používá k hledání zjišťování služby odpovídající konkrétní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d22b9-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="d22b9-110">Aktivita s kódem výstupy identifikátor URI, který se používá později pomocí aktivity odeslání.</span><span class="sxs-lookup"><span data-stu-id="d22b9-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d22b9-111">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="d22b9-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d22b9-112">Tato ukázka používá koncové body HTTP, které musí mít odpovídající seznamy ACL adresu URL pro spuštění (viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti).</span><span class="sxs-lookup"><span data-stu-id="d22b9-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="d22b9-113">Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="d22b9-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="d22b9-114">Nahraďte doména a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.</span><span class="sxs-lookup"><span data-stu-id="d22b9-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="d22b9-115">**netsh http přidat adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="d22b9-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d22b9-116">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="d22b9-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d22b9-117">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d22b9-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d22b9-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d22b9-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d22b9-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d22b9-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
