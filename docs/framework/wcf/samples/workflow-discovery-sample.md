---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143483"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="37188-102">Ukázka zjišťování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="37188-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="37188-103">Tato ukázka ukazuje, jak zjistit službu pracovního postupu a jak vytvořit vlastní aktivitu kódu, která vyhledá konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="37188-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="37188-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="37188-104">Demonstrates</span></span>  
 <span data-ttu-id="37188-105">Zjišťování aktivity hledání a využití pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="37188-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="37188-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="37188-106">Discussion</span></span>  
 <span data-ttu-id="37188-107">V první části ukázky je služba pracovního postupu zjistitelná pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="37188-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="37188-108">Konfiguraci lze také použít k použití služby odpovídajícím způsobem s vlastní metadata (například obory).</span><span class="sxs-lookup"><span data-stu-id="37188-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="37188-109">Na straně klienta ukázka používá vlastní kód aktivity, která používá Zjišťování k vyhledání služby odpovídající konkrétní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="37188-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="37188-110">Aktivita kódu vyvezuje identifikátor URI, který je později používán aktivitou odesílání.</span><span class="sxs-lookup"><span data-stu-id="37188-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37188-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="37188-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="37188-112">Tato ukázka používá koncové body HTTP, které musí mít správné adresy ACL správné adresy URL ke spuštění (podrobnosti naleznete [v tématu Konfigurace protokolu HTTP a HTTPS).](../feature-details/configuring-http-and-https.md)</span><span class="sxs-lookup"><span data-stu-id="37188-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="37188-113">Provedení následujícího příkazu na příkazovém řádku se zvýšenými oprávněními by mělo přidat příslušné akly.</span><span class="sxs-lookup"><span data-stu-id="37188-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="37188-114">Pokud prostředí nerozumí formátu proměnné, nahraďte doménu a uživatelské jméno následujícími argumenty.</span><span class="sxs-lookup"><span data-stu-id="37188-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
     <span data-ttu-id="37188-115">**netsh http přidat urlacl url=http://+:8000/ \\user=%DOMAIN% %UserName%**</span><span class="sxs-lookup"><span data-stu-id="37188-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37188-116">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="37188-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37188-117">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="37188-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="37188-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="37188-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37188-119">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="37188-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
