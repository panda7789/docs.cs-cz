---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 67e719afd40b52f37c777cf9791291a16878592f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600085"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="6e057-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="6e057-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="6e057-103">Tato ukázka demonstruje nutnost a důsledky použití režimu ConcurrencyMode. předaných do implementace služby.</span><span class="sxs-lookup"><span data-stu-id="6e057-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="6e057-104">Režim ConcurrencyMode. reonly to znamená, že služba (nebo zpětné volání) zpracovává v daném okamžiku pouze jednu zprávu (podobnou `ConcurencyMode.Single` ).</span><span class="sxs-lookup"><span data-stu-id="6e057-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="6e057-105">Pro zajištění bezpečnosti vlákna Windows Communication Foundation (WCF) zamkne `InstanceContext` zpracování zprávy, aby nemohly být zpracovány žádné další zprávy.</span><span class="sxs-lookup"><span data-stu-id="6e057-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="6e057-106">V případě režimu vícenásobného vstupu `InstanceContext` je odemčení těsně před tím, než služba odešle odchozí volání, čímž umožní následné volání (které se dá znovu využít v ukázce), aby se zámek při příštím výskytu služby dostal.</span><span class="sxs-lookup"><span data-stu-id="6e057-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="6e057-107">K předvedení tohoto chování Ukázka ukazuje, jak může klient a služba mezi sebou posílat zprávy pomocí duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6e057-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="6e057-108">Definovaná smlouva je duplexní kontrakt s metodou, kterou `Ping` Služba implementuje, a metodou zpětného volání, `Pong` kterou klient implementuje.</span><span class="sxs-lookup"><span data-stu-id="6e057-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="6e057-109">Klient vyvolá `Ping` metodu serveru s počtem impulsů, čímž iniciuje volání.</span><span class="sxs-lookup"><span data-stu-id="6e057-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="6e057-110">Služba kontroluje, zda počet impulsů není roven 0, a poté vyvolá metodu zpětného volání `Pong` při snížení počtu impulsů.</span><span class="sxs-lookup"><span data-stu-id="6e057-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="6e057-111">To se provádí v ukázce v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6e057-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Implementace zpětného volání `Pong` má stejnou logiku jako `Ping` implementace. To znamená, že kontroluje, zda počet impulsů není nula, a poté vyvolá `Ping` metodu na kanálu zpětného volání (v tomto případě je to kanál, který byl použit k odeslání původní `Ping` zprávy) s počtem impulsů sníženým o 1. Okamžik, kdy počet impulsů dosáhne 0, metoda se vrátí a rozbalí všechny odpovědi zpět na první volání provedené klientem, který iniciuje volání. <span data-ttu-id="6e057-115">Tento příklad je zobrazen v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6e057-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Jak metody, tak `Ping` `Pong` jsou požadavky a odpovědi, což znamená, že první volání vrátí, `Ping` dokud volání `CallbackChannel<T>.Pong()` nevrátí. Na straně klienta `Pong` nemůže metoda vracet, dokud nebude `Ping` vráceno další volání. <span data-ttu-id="6e057-118">Vzhledem k tomu, že zpětné volání a služba musí učinit odchozí volání požadavků a odpovědí předtím, než mohou odpovědět na nevyřízenou žádost, musí být obě implementace označeny chováním režim ConcurrencyMode. replatformed.</span><span class="sxs-lookup"><span data-stu-id="6e057-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6e057-119">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="6e057-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6e057-120">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e057-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6e057-121">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e057-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6e057-122">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e057-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6e057-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="6e057-123">Demonstrates</span></span>  
 <span data-ttu-id="6e057-124">Chcete-li spustit ukázku, sestavte klientské a serverové projekty.</span><span class="sxs-lookup"><span data-stu-id="6e057-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="6e057-125">Pak otevřete dvě okna příkazů a změňte adresáře na \<sample> adresáře \CS\Service\bin\debug a \<sample> \CS\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="6e057-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="6e057-126">Poté spusťte službu tak, že zadáte `service.exe` a potom vyvoláte Client. exe s počáteční hodnotou tiků předaných jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="6e057-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="6e057-127">Zobrazí se ukázkový výstup pro 10 taktů.</span><span class="sxs-lookup"><span data-stu-id="6e057-127">A sample output for 10 ticks is shown.</span></span>  
  
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
> <span data-ttu-id="6e057-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="6e057-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6e057-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6e057-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6e057-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="6e057-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e057-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6e057-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
