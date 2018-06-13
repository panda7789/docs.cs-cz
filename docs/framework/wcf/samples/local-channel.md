---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501504"
---
# <a name="local-channel"></a><span data-ttu-id="3dfd5-102">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="3dfd5-102">Local Channel</span></span>
<span data-ttu-id="3dfd5-103">Místní kanál je přenos kanálu Windows Communication Foundation (WCF), který se používá pro komunikaci v rámci stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="3dfd5-104">To je užitečné pro scénáře, kde klient a služba běží ve stejné doméně aplikace a je třeba se vyhnout režii typické kanál zásobníku WCF (serializace a deserializace zpráv).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3dfd5-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="3dfd5-105">Demonstrates</span></span>  
 <span data-ttu-id="3dfd5-106">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="3dfd5-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3dfd5-107">Diskusní</span><span class="sxs-lookup"><span data-stu-id="3dfd5-107">Discussion</span></span>  
 <span data-ttu-id="3dfd5-108">Ukázkový soubor obsahuje dva soubory projektu:</span><span class="sxs-lookup"><span data-stu-id="3dfd5-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="3dfd5-109">**LocalChannel**: programové reprezentace místní kanál v rámci aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="3dfd5-110">V tomto projektu komponentu odesílání umístí zprávu do fronty v paměti a komponentu přijímající zrušte fronty na zprávu, aby ji přijmou.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="3dfd5-111">**ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a poté spustí klienta k volání služby ze stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="3dfd5-112">Místní kanál návrhu přeskočí zásobníku kanál a zvýšit rychlost proces serializace.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="3dfd5-113">Kanál místní přenosu se implementuje pomocí fronty přenosu volání služby z klienta ke službě a vrátí hodnotu zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="3dfd5-114">Místo serializaci parametry a návratové hodnoty, zkopíruje ukázce objekty.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3dfd5-115">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3dfd5-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3dfd5-116">Sestavte a spusťte LocalChannel řešení.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="3dfd5-117">Hostitel služby je spuštěná a klient zavolá službu pomocí místní kanál.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="3dfd5-118">Výsledky volání služby se zobrazí okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3dfd5-119">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3dfd5-120">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3dfd5-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3dfd5-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
