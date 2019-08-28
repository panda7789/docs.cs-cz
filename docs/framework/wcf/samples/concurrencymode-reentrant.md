---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040145"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="25bd9-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="25bd9-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="25bd9-103">Tato ukázka demonstruje nutnost a důsledky použití režimu ConcurrencyMode. předaných do implementace služby.</span><span class="sxs-lookup"><span data-stu-id="25bd9-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="25bd9-104">Režim ConcurrencyMode. reonly to znamená, že služba (nebo zpětné volání) zpracovává v daném okamžiku pouze jednu zprávu ( `ConcurencyMode.Single`podobnou).</span><span class="sxs-lookup"><span data-stu-id="25bd9-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="25bd9-105">Pro zajištění bezpečnosti vlákna Windows Communication Foundation (WCF) zamkne `InstanceContext` zpracování zprávy, aby nemohly být zpracovány žádné další zprávy.</span><span class="sxs-lookup"><span data-stu-id="25bd9-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="25bd9-106">V případě režimu `InstanceContext` vícenásobného vstupu je odemčení těsně před tím, než služba odešle odchozí volání, čímž umožní následné volání (které se dá znovu využít v ukázce), aby se zámek při příštím výskytu služby dostal.</span><span class="sxs-lookup"><span data-stu-id="25bd9-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="25bd9-107">K předvedení tohoto chování Ukázka ukazuje, jak může klient a služba mezi sebou posílat zprávy pomocí duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="25bd9-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="25bd9-108">Definovaná smlouva je duplexní kontrakt s `Ping` metodou, kterou služba implementuje, a metodou `Pong` zpětného volání, kterou klient implementuje.</span><span class="sxs-lookup"><span data-stu-id="25bd9-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="25bd9-109">Klient vyvolá `Ping` metodu serveru s počtem impulsů, čímž iniciuje volání.</span><span class="sxs-lookup"><span data-stu-id="25bd9-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="25bd9-110">Služba kontroluje, zda počet impulsů není roven 0, a poté vyvolá `Pong` metodu zpětného volání při snížení počtu impulsů.</span><span class="sxs-lookup"><span data-stu-id="25bd9-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="25bd9-111">To se provádí v ukázce v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="25bd9-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 `Pong` Implementace zpětného volání má stejnou logiku `Ping` jako implementace. To znamená, že kontroluje, zda počet impulsů není nula, a poté vyvolá `Ping` metodu na kanálu zpětného volání (v tomto případě je to kanál, který byl použit k odeslání původní `Ping` zprávy) s počtem impulsů sníženým o 1. Okamžik, kdy počet impulsů dosáhne 0, metoda se vrátí a rozbalí všechny odpovědi zpět na první volání provedené klientem, který iniciuje volání. <span data-ttu-id="25bd9-115">Tento příklad je zobrazen v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="25bd9-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Jak metody, `Pong` tak jsou požadavky `Ping` `CallbackChannel<T>.Pong()`aodpovědi , což znamená, že první volání vrátí, dokud volání nevrátí. `Ping` Na straně klienta `Pong` nemůže metoda vracet, dokud nebude vráceno `Ping` další volání. <span data-ttu-id="25bd9-118">Vzhledem k tomu, že zpětné volání a služba musí učinit odchozí volání požadavků a odpovědí předtím, než mohou odpovědět na nevyřízenou žádost, musí být obě implementace označeny chováním režim ConcurrencyMode. replatformed.</span><span class="sxs-lookup"><span data-stu-id="25bd9-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25bd9-119">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="25bd9-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="25bd9-120">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25bd9-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="25bd9-121">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25bd9-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="25bd9-122">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25bd9-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="25bd9-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="25bd9-123">Demonstrates</span></span>  
 <span data-ttu-id="25bd9-124">Chcete-li spustit ukázku, sestavte klientské a serverové projekty.</span><span class="sxs-lookup"><span data-stu-id="25bd9-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="25bd9-125">Pak otevřete dvě okna příkazů a změňte adresáře na \<vzorový > \CS\Service\bin\debug a \<Sample > \CS\Client\bin\debug adresáře.</span><span class="sxs-lookup"><span data-stu-id="25bd9-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="25bd9-126">Poté spusťte službu tak, že `service.exe` zadáte a potom vyvoláte Client. exe s počáteční hodnotou tiků předaných jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="25bd9-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="25bd9-127">Zobrazí se ukázkový výstup pro 10 taktů.</span><span class="sxs-lookup"><span data-stu-id="25bd9-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="25bd9-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="25bd9-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="25bd9-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="25bd9-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="25bd9-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="25bd9-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25bd9-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="25bd9-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
