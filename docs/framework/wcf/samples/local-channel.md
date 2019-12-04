---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714887"
---
# <a name="local-channel"></a><span data-ttu-id="d50b8-102">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="d50b8-102">Local Channel</span></span>
<span data-ttu-id="d50b8-103">Místní kanál je transportní kanál Windows Communication Foundation (WCF), který se používá ke komunikaci ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d50b8-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="d50b8-104">To je užitečné ve scénářích, kdy klient a služba běží ve stejné aplikační doméně a režie typického zásobníku kanálu WCF (serializace a deserializace zpráv) se musí vyhnout.</span><span class="sxs-lookup"><span data-stu-id="d50b8-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d50b8-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="d50b8-105">Demonstrates</span></span>  
 <span data-ttu-id="d50b8-106">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="d50b8-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d50b8-107">Účely</span><span class="sxs-lookup"><span data-stu-id="d50b8-107">Discussion</span></span>  
 <span data-ttu-id="d50b8-108">Ukázka se skládá ze dvou souborů projektu:</span><span class="sxs-lookup"><span data-stu-id="d50b8-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="d50b8-109">**LocalChannel**: Programová reprezentace místního kanálu v rámci aktuální domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d50b8-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="d50b8-110">V tomto projektu součást odeslání umístí zprávu do fronty v paměti a přijímající součást rozřadí zprávu k jejímu přijetí.</span><span class="sxs-lookup"><span data-stu-id="d50b8-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="d50b8-111">**ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a potom spustí klienta, který bude volat službu ze stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d50b8-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="d50b8-112">Návrh místního kanálu přeskočí zásobník kanálů a proces serializace, aby se zvýšila rychlost.</span><span class="sxs-lookup"><span data-stu-id="d50b8-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="d50b8-113">Místní transportní kanál je implementován pomocí fronty pro přenos volání služby od klienta ke službě a vrácení hodnoty zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="d50b8-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="d50b8-114">Místo serializace parametrů a vrácených hodnot ukázka kopíruje objekty.</span><span class="sxs-lookup"><span data-stu-id="d50b8-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d50b8-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d50b8-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d50b8-116">Sestavte a spusťte řešení LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="d50b8-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="d50b8-117">Hostitel služby je spuštěn a klient volá službu pomocí místního kanálu.</span><span class="sxs-lookup"><span data-stu-id="d50b8-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="d50b8-118">Zobrazí se okno konzoly pro zobrazení výsledků volání služby.</span><span class="sxs-lookup"><span data-stu-id="d50b8-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d50b8-119">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d50b8-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d50b8-120">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d50b8-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d50b8-121">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="d50b8-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d50b8-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d50b8-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
