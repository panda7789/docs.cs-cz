---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b503e6231741fb049dbd8e9fdaae73c127ceaa51
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714998"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="8494c-102">Ukázka zjišťování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8494c-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="8494c-103">V této ukázce se dozvíte, jak vytvořit službu pracovního postupu a jak vytvořit vlastní aktivitu kódu, která vyhledává konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="8494c-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8494c-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="8494c-104">Demonstrates</span></span>  
 <span data-ttu-id="8494c-105">Vyhledání aktivity a využití pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8494c-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8494c-106">Účely</span><span class="sxs-lookup"><span data-stu-id="8494c-106">Discussion</span></span>  
 <span data-ttu-id="8494c-107">V první části ukázky se služba pracovního postupu provedla zjistitelným použitím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8494c-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="8494c-108">Konfiguraci je také možné použít k odpovídajícímu uplatnění služby s vlastními metadaty (například obory).</span><span class="sxs-lookup"><span data-stu-id="8494c-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="8494c-109">V klientovi ukázka používá vlastní aktivitu kódu, která používá zjišťování k vyhledání služby, která odpovídá konkrétnímu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8494c-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="8494c-110">Aktivita kódu má za výstupem identifikátor URI, který je později používán aktivitou odeslání.</span><span class="sxs-lookup"><span data-stu-id="8494c-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8494c-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8494c-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8494c-112">Tato ukázka používá koncové body HTTP, které musí mít správné seznamy ACL adres URL pro spuštění (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ).</span><span class="sxs-lookup"><span data-stu-id="8494c-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="8494c-113">Provedením následujícího příkazu na příkazovém řádku se zvýšenými oprávněními by se měly přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="8494c-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="8494c-114">Pokud vaše prostředí nerozumí formátu proměnné, nahraďte doménu a uživatelské jméno pro následující argumenty.</span><span class="sxs-lookup"><span data-stu-id="8494c-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="8494c-115">**netsh http Add urlacl URL =http://+:8000/ uživatel =% DOMAIN%\\ % UserName%**</span><span class="sxs-lookup"><span data-stu-id="8494c-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8494c-116">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8494c-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8494c-117">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8494c-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8494c-118">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="8494c-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8494c-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8494c-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
