---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144504"
---
# <a name="local-channel"></a><span data-ttu-id="c9a1e-102">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="c9a1e-102">Local Channel</span></span>
<span data-ttu-id="c9a1e-103">Místní kanál je přenosový kanál WCF (Windows Communication Foundation), který se používá pro komunikaci v rámci stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="c9a1e-104">To je užitečné pro scénáře, kde klient a služba jsou spuštěny ve stejné doméně aplikace a je třeba se vyhnout režii typického zásobníku kanálu WCF (serializace a deserializace zpráv).</span><span class="sxs-lookup"><span data-stu-id="c9a1e-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c9a1e-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="c9a1e-105">Demonstrates</span></span>  
 <span data-ttu-id="c9a1e-106">Místní kanál</span><span class="sxs-lookup"><span data-stu-id="c9a1e-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c9a1e-107">Diskuse</span><span class="sxs-lookup"><span data-stu-id="c9a1e-107">Discussion</span></span>  
 <span data-ttu-id="c9a1e-108">Ukázka se skládá ze dvou souborů projektu:</span><span class="sxs-lookup"><span data-stu-id="c9a1e-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="c9a1e-109">**LocalChannel**: Programová reprezentace místního kanálu v rámci aktuální domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="c9a1e-110">V tomto projektu odesílající součást umístí zprávu do fronty v paměti a přijímající součást odřadí zprávu do fronty, aby ji přijala.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="c9a1e-111">**ClientAndService**: Tento projekt je hostitelem služby v konzolové aplikaci a potom spustí klienta pro volání služby ze stejné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="c9a1e-112">Návrh místního kanálu přeskočí zásobník kanálu i proces serializace, aby se zvýšila rychlost.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="c9a1e-113">Kanál místního přenosu je implementován pomocí fronty k přenosu volání služby z klienta do služby a vrátit hodnotu klientovi zpět.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="c9a1e-114">Místo serializace parametrů a vrácených hodnot ukázka objekty zkopíruje.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9a1e-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c9a1e-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c9a1e-116">Sestavení a spuštění řešení LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="c9a1e-117">Hostitel služby je spuštěn a klient volá službu pomocí místního kanálu.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="c9a1e-118">Zobrazí se okno konzoly zobrazující výsledky volání služby.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9a1e-119">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c9a1e-120">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c9a1e-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9a1e-122">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c9a1e-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
