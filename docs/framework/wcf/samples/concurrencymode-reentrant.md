---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 94ea62d18fec202a099c2797602224eab43299b4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202013"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="bee15-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="bee15-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="bee15-103">Tento příklad znázorňuje nutnost a důsledky použití ConcurrencyMode.Reentrant na implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="bee15-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="bee15-104">ConcurrencyMode.Reentrant znamená, že služba (nebo zpětného volání) zpracovává pouze jednu zprávu v daném okamžiku (obdobná `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="bee15-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="bee15-105">K zajištění bezpečnosti vlákna, uzamkne Windows Communication Foundation (WCF) `InstanceContext` zpracovává zprávu tak, aby zpracovat žádné další zprávy.</span><span class="sxs-lookup"><span data-stu-id="bee15-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="bee15-106">V případě vícenásobné režim `InstanceContext` odemknut těsně před plánovaným začátkem služby umožňuje odchozí volání a tím umožní následných volání (může to být vícenásobné, jak je uvedeno v ukázce) se získat zámek příště je k dispozici ve službě.</span><span class="sxs-lookup"><span data-stu-id="bee15-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="bee15-107">Abychom si předvedli chování, tato ukázka vysvětluje, jak může klient a služba odesílání zpráv mezi sebou pomocí duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="bee15-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="bee15-108">Duplexní kontrakt s je kontrakt definovaný `Ping` implementování službou a metoda zpětného volání metody `Pong` implementování klientem.</span><span class="sxs-lookup"><span data-stu-id="bee15-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="bee15-109">Klient vyvolá serveru `Ping` metodu s čárka počítat, a tím inicializace volání.</span><span class="sxs-lookup"><span data-stu-id="bee15-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="bee15-110">Služba zkontroluje, zda počet impulsů není roven 0 a poté vyvolá tak potřebná zpětná volání `Pong` metoda při dekrementace počtu impulsů.</span><span class="sxs-lookup"><span data-stu-id="bee15-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="bee15-111">To se provádí v následujícím kódu v ukázce.</span><span class="sxs-lookup"><span data-stu-id="bee15-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Při zpětném volání `Pong` implementace má stejnou logikou jako `Ping` implementace. To znamená, zkontroluje, zda počet impulsů není nula a potom vyvolá `Ping` metoda zpětného volání kanálu (v tomto případě je kanál, který jste použili k zaslání původní `Ping` zpráva) pomocí značek počet sníží o 1. V okamžiku, kdy počet impulsů dosáhne hodnoty 0, vrátí tato metoda hodnotu a rozbalení všechny odpovědi zpátky na první volání, která iniciovala volání klienta. <span data-ttu-id="bee15-115">To je ukázáno v implementaci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bee15-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Jak `Ping` a `Pong` metody jsou požadavku/odpovědi, což znamená, že první volání `Ping` nevrací až do volání `CallbackChannel<T>.Pong()` vrátí. V klientském počítači `Pong` metoda nemůže vrátit až do další `Ping` volání, že ji nastavit na vrátí. <span data-ttu-id="bee15-118">Protože zpětné volání a služba musí volat odchozí požadavek/odpověď předtím, než můžete odpovědět čekající žádosti, musí být obě implementace označeny ConcurrencyMode.Reentrant chování.</span><span class="sxs-lookup"><span data-stu-id="bee15-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bee15-119">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bee15-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bee15-120">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bee15-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bee15-121">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bee15-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bee15-122">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bee15-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bee15-123">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="bee15-123">Demonstrates</span></span>  
 <span data-ttu-id="bee15-124">Ke spuštění ukázky, sestavení projektů klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="bee15-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="bee15-125">Pak otevřete dvě okně příkazového řádku a přejděte do adresáře \<ukázka > \CS\Service\bin\debug a \<ukázka > \CS\Client\bin\debug adresáře.</span><span class="sxs-lookup"><span data-stu-id="bee15-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="bee15-126">Potom spusťte služby zadáním `service.exe` a pak vyvolejte Client.exe s počáteční hodnotou ticks předaný jako vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="bee15-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="bee15-127">Ukázkový výstup pro 10 impulzech se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bee15-127">A sample output for 10 ticks is shown.</span></span>  
  
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
>  <span data-ttu-id="bee15-128">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bee15-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bee15-129">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bee15-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bee15-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bee15-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bee15-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bee15-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="bee15-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="bee15-132">See Also</span></span>
