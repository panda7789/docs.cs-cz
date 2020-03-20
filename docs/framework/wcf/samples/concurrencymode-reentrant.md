---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183898"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Tato ukázka ukazuje nutnost a důsledky použití ConcurrencyMode.Reentrant na implementaci služby. ConcurrencyMode.Reentrant znamená, že služba (nebo zpětné volání) zpracovává pouze jednu `ConcurencyMode.Single`zprávu v daném okamžiku (analogicky k). Chcete-li zajistit bezpečnost podprocesu, Windows `InstanceContext` Communication Foundation (WCF) uzamkne zpracování zprávy tak, aby žádné jiné zprávy mohou být zpracovány. V případě režimu Reentrant `InstanceContext` je odemčentěsně před tím, než služba provede odchozí volání, čímž umožní následnému volání (které může být reentrant, jak je znázorněno v ukázce), získat zámek při příštím příchozím do služby. Chcete-li demonstrovat chování, ukázka ukazuje, jak klient a služba můžete odesílat zprávy mezi sebou pomocí duplexní smlouvy.  
  
 Definovaná smlouva je duplexní `Ping` smlouva s metodou implementovanou `Pong` službou a metodou zpětného volání implementovanou klientem. Klient vyvolá `Ping` metodu serveru s počtem značek a tím iniciuje volání. Služba zkontroluje, zda počet značek není rovna 0 a `Pong` potom vyvolá metodu zpětná volání při snížení počtu značek. To se provádí podle následujícího kódu v ukázce.  
  
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
  
 Implementace zpětného `Pong` volání má stejnou logiku `Ping` jako implementace. To znamená, že zkontroluje, zda počet značek `Ping` není nula a potom vyvolá metodu na kanálu zpětného volání `Ping` (v tomto případě je kanál, který byl použit k odeslání původní zprávy) s počet značek snížena o 1. V okamžiku, kdy počet značek dosáhne 0, metoda vrátí a tím rozbalí všechny odpovědi zpět na první volání provedené klientem, který inicioval volání. To je zobrazeno v implementaci zpětného volání.  
  
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
  
 Obě `Ping` metody `Pong` a jsou request/reply, což znamená, že první `Ping` volání `CallbackChannel<T>.Pong()` nevrátí, dokud volání vrátí. Na straně klienta `Pong` metoda nemůže `Ping` vrátit až do další volání, které se vrátí. Vzhledem k tomu, že zpětné volání a služba musí provést odchozí požadavek/odpověď volání před tím, než mohou odpovědět na čekající požadavek, obě implementace musí být označeny concurrencyMode.Reentrant chování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstruje  
 Chcete-li spustit ukázku, vytvořte projekty klienta a serveru. Potom otevřete dvě okna příkazů a \<změňte adresáře na ukázkový \<>\CS\Service\bin\debug a ukázkové>\CS\Client\bin\debug adresáře. Potom spusťte službu zadáním `service.exe` a potom vyvolat Client.exe s počáteční hodnotou značek předaných jako vstupní argument. Ukázkový výstup pro 10 značek je zobrazen.  
  
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
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
