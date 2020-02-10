---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cd91a171f3242cfd7e8ac0404e24ac065919bcce
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094615"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="20b7d-102">Korelace dotazů zprávy LINQ</span><span class="sxs-lookup"><span data-stu-id="20b7d-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="20b7d-103">Tato ukázka předvádí, jak provést korelaci založenou na obsahu pomocí vlastní implementace <xref:System.ServiceModel.Dispatcher.MessageQuery>, a to na rozdíl od <xref:System.ServiceModel.XPathMessageQuery>poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="20b7d-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="20b7d-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="20b7d-104">Demonstrates</span></span>  
 <span data-ttu-id="20b7d-105">Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="20b7d-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="20b7d-106">Účely</span><span class="sxs-lookup"><span data-stu-id="20b7d-106">Discussion</span></span>  
 <span data-ttu-id="20b7d-107">Tento příklad ukazuje, jak lze od <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třídy pro účely korelace roztáhnout.</span><span class="sxs-lookup"><span data-stu-id="20b7d-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="20b7d-108">Vlastní implementace, `LinqMessageQuery`, umožňuje uživatelům poskytnout XName k hledání ve zprávě pomocí XLinq.</span><span class="sxs-lookup"><span data-stu-id="20b7d-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="20b7d-109">Data načtená dotazem slouží k vytvoření korelačního klíče pro odeslání zpráv do příslušné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b7d-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20b7d-110">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="20b7d-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="20b7d-111">Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP.</span><span class="sxs-lookup"><span data-stu-id="20b7d-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="20b7d-112">Pokud chcete tuto ukázku spustit, musí se přidat správné seznamy ACL adresy URL (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](../../wcf/feature-details/configuring-http-and-https.md) ), a to buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními, abyste přidali příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="20b7d-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="20b7d-113">Ujistěte se, že je nahrazena vaše doména a uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="20b7d-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="20b7d-114">Po přidání seznamů ACL adresy URL použijte následující postup.</span><span class="sxs-lookup"><span data-stu-id="20b7d-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="20b7d-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="20b7d-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="20b7d-116">Nastavte více spouštěcích projektů kliknutím pravým tlačítkem na řešení a výběrem možnosti **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="20b7d-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="20b7d-117">Přidejte **službu** a **klienta** (v tomto pořadí) jako několik spouštěcích projektů.</span><span class="sxs-lookup"><span data-stu-id="20b7d-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="20b7d-118">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="20b7d-118">Run the application.</span></span> <span data-ttu-id="20b7d-119">Konzola klienta zobrazuje pracovní postup odesílající objednávku a příjem ID nákupní objednávky a následně potvrzuje objednávku.</span><span class="sxs-lookup"><span data-stu-id="20b7d-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="20b7d-120">V okně služby se zobrazí zpracovávané požadavky.</span><span class="sxs-lookup"><span data-stu-id="20b7d-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20b7d-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="20b7d-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20b7d-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="20b7d-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="20b7d-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="20b7d-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20b7d-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="20b7d-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
