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
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Tato ukázka demonstruje nutnost a důsledky použití režimu ConcurrencyMode. předaných do implementace služby. Režim ConcurrencyMode. reonly to znamená, že služba (nebo zpětné volání) zpracovává v daném okamžiku pouze jednu zprávu (s analogovou `ConcurencyMode.Single`). Pro zajištění bezpečnosti vlákna Windows Communication Foundation (WCF) zamkne `InstanceContext` zpracování zprávy, aby nemohly být zpracovány žádné další zprávy. V případě režimu opakovaného vstupu se `InstanceContext` odemkne těsně před tím, než služba odešle odchozí volání, a tím umožní následné volání (které se dá znovu využít v ukázce) a získá zámek k dalšímu přihlášení ke službě. K předvedení tohoto chování Ukázka ukazuje, jak může klient a služba mezi sebou posílat zprávy pomocí duplexního kontraktu.  
  
 Definovaná smlouva je duplexní smlouva se `Ping` metodou, kterou služba implementuje, a metodou zpětného volání `Pong` implementovaná klientem. Klient vyvolá metodu `Ping` serveru s počtem impulsů, čímž iniciuje volání. Služba zkontroluje, zda se počet impulsů nerovná 0, a poté vyvolá zpětná volání `Pong` metodou při snížení počtu impulsů. To se provádí v ukázce v následujícím kódu.  
  
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
  
 Implementace `Pong` zpětného volání má stejnou logiku jako implementace `Ping`. To znamená, že kontroluje, zda počet impulsů není nula, a poté vyvolá metodu `Ping` na kanálu zpětného volání (v tomto případě je to kanál, který byl použit k odeslání původní `Ping` zprávy) s počtem impulsů sníženým o 1. Okamžik, kdy počet impulsů dosáhne 0, metoda se vrátí a rozbalí všechny odpovědi zpět na první volání provedené klientem, který iniciuje volání. Tento příklad je zobrazen v implementaci zpětného volání.  
  
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
  
 Metody `Ping` i `Pong` jsou požadavky a odpovědi, což znamená, že první volání `Ping` nevrátí, dokud volání `CallbackChannel<T>.Pong()` nevrátí. Na straně klienta nemůže metoda `Pong` vrátit, dokud nebude vráceno další `Ping` volání. Vzhledem k tomu, že zpětné volání a služba musí učinit odchozí volání požadavků a odpovědí předtím, než mohou odpovědět na nevyřízenou žádost, musí být obě implementace označeny chováním režim ConcurrencyMode. replatformed.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstruje  
 Chcete-li spustit ukázku, sestavte klientské a serverové projekty. Pak otevřete dvě okna příkazů a změňte adresáře na \<Sample > \CS\Service\bin\debug a \<ukázkových adresářů > \CS\Client\bin\debug. Poté spusťte službu zadáním `service.exe` a potom volejte soubor Client. exe s počáteční hodnotou tiků předaných jako vstupní argument. Zobrazí se ukázkový výstup pro 10 taktů.  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
