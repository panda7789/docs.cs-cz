---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182808"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="d6d0c-102">Korelace dotazů zprávy LINQ</span><span class="sxs-lookup"><span data-stu-id="d6d0c-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="d6d0c-103">Tato ukázka ukazuje, jak provést korelaci <xref:System.ServiceModel.Dispatcher.MessageQuery> založenou na obsahu pomocí <xref:System.ServiceModel.XPathMessageQuery>vlastní implementace na rozdíl od poskytovaného systému .</span><span class="sxs-lookup"><span data-stu-id="d6d0c-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d6d0c-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="d6d0c-104">Demonstrates</span></span>  
 <span data-ttu-id="d6d0c-105">Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>korelace založená na obsahu.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d6d0c-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="d6d0c-106">Discussion</span></span>  
 <span data-ttu-id="d6d0c-107">Tato ukázka ukazuje, <xref:System.ServiceModel.Dispatcher.MessageQuery> jak rozšířit ze základní třídy pro účely korelace.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="d6d0c-108">Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="d6d0c-109">Data načtená dotazem se používají k vytvoření klíče korelace pro odeslání zpráv do příslušné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6d0c-110">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d6d0c-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d6d0c-111">Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="d6d0c-112">Chcete-li spustit tuto ukázku, musí být přidány správné adresy ACL správné adresy URL (viz [Konfigurace protokolu HTTP a HTTPS](../../wcf/feature-details/configuring-http-and-https.md) podrobnosti), buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu ve zvýšené výzvě k přidání příslušných seznamu ACL.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="d6d0c-113">Ujistěte se, že vaše doména a uživatelské jméno jsou nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="d6d0c-114">Po přidání adres URL aklů použijte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="d6d0c-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="d6d0c-116">Nastavte více počátečních projektů klepnutím pravým tlačítkem myši na řešení a výběrem **možnosti Nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="d6d0c-117">Přidejte **službu** a **klienta** (v tomto pořadí) jako více start-up projektů.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="d6d0c-118">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-118">Run the application.</span></span> <span data-ttu-id="d6d0c-119">Klientská konzola zobrazuje pracovní postup, který odesílá objednávku a přijímá ID nákupní objednávky a následně objednávku potvrzuje.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="d6d0c-120">Okno Služba zobrazí zpracovávané požadavky.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6d0c-121">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6d0c-122">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d6d0c-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6d0c-124">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d6d0c-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
