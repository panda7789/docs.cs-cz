---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 0ac3b811c59abfbb3148ddad3d518443f7633adc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714969"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="1c014-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="1c014-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="1c014-103">Tato ukázka demonstruje nutnost a důsledky použití režimu ConcurrencyMode. předaných do implementace služby.</span><span class="sxs-lookup"><span data-stu-id="1c014-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="1c014-104">Režim ConcurrencyMode. reonly to znamená, že služba (nebo zpětné volání) zpracovává v daném okamžiku pouze jednu zprávu (s analogovou `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="1c014-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="1c014-105">Pro zajištění bezpečnosti vlákna Windows Communication Foundation (WCF) zamkne `InstanceContext` zpracování zprávy, aby nemohly být zpracovány žádné další zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c014-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="1c014-106">V případě režimu opakovaného vstupu se `InstanceContext` odemkne těsně před tím, než služba odešle odchozí volání, a tím umožní následné volání (které se dá znovu využít v ukázce) a získá zámek k dalšímu přihlášení ke službě.</span><span class="sxs-lookup"><span data-stu-id="1c014-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="1c014-107">K předvedení tohoto chování Ukázka ukazuje, jak může klient a služba mezi sebou posílat zprávy pomocí duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1c014-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="1c014-108">Definovaná smlouva je duplexní smlouva se `Ping` metodou, kterou služba implementuje, a metodou zpětného volání `Pong` implementovaná klientem.</span><span class="sxs-lookup"><span data-stu-id="1c014-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="1c014-109">Klient vyvolá metodu `Ping` serveru s počtem impulsů, čímž iniciuje volání.</span><span class="sxs-lookup"><span data-stu-id="1c014-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="1c014-110">Služba zkontroluje, zda se počet impulsů nerovná 0, a poté vyvolá zpětná volání `Pong` metodou při snížení počtu impulsů.</span><span class="sxs-lookup"><span data-stu-id="1c014-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="1c014-111">To se provádí v ukázce v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1c014-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Implementace `Pong` zpětného volání má stejnou logiku jako implementace `Ping`. To znamená, že kontroluje, zda počet impulsů není nula, a poté vyvolá metodu `Ping` na kanálu zpětného volání (v tomto případě je to kanál, který byl použit k odeslání původní `Ping` zprávy) s počtem impulsů sníženým o 1. Okamžik, kdy počet impulsů dosáhne 0, metoda se vrátí a rozbalí všechny odpovědi zpět na první volání provedené klientem, který iniciuje volání. <span data-ttu-id="1c014-115">Tento příklad je zobrazen v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1c014-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Metody `Ping` i `Pong` jsou požadavky a odpovědi, což znamená, že první volání `Ping` nevrátí, dokud volání `CallbackChannel<T>.Pong()` nevrátí. Na straně klienta nemůže metoda `Pong` vrátit, dokud nebude vráceno další `Ping` volání. <span data-ttu-id="1c014-118">Vzhledem k tomu, že zpětné volání a služba musí učinit odchozí volání požadavků a odpovědí předtím, než mohou odpovědět na nevyřízenou žádost, musí být obě implementace označeny chováním režim ConcurrencyMode. replatformed.</span><span class="sxs-lookup"><span data-stu-id="1c014-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1c014-119">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1c014-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1c014-120">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1c014-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1c014-121">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1c014-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1c014-122">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1c014-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1c014-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="1c014-123">Demonstrates</span></span>  
 <span data-ttu-id="1c014-124">Chcete-li spustit ukázku, sestavte klientské a serverové projekty.</span><span class="sxs-lookup"><span data-stu-id="1c014-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="1c014-125">Pak otevřete dvě okna příkazů a změňte adresáře na \<Sample > \CS\Service\bin\debug a \<ukázkových adresářů > \CS\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="1c014-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="1c014-126">Poté spusťte službu zadáním `service.exe` a potom volejte soubor Client. exe s počáteční hodnotou tiků předaných jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="1c014-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="1c014-127">Zobrazí se ukázkový výstup pro 10 taktů.</span><span class="sxs-lookup"><span data-stu-id="1c014-127">A sample output for 10 ticks is shown.</span></span>  
  
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
> <span data-ttu-id="1c014-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="1c014-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1c014-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="1c014-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1c014-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="1c014-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1c014-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1c014-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
