---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 49ef172c607957ad68b628a82d26edbb371522e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549097"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Tento příklad znázorňuje nutnost a důsledky použití ConcurrencyMode.Reentrant na implementaci služby. ConcurrencyMode.Reentrant znamená, že služba (nebo zpětného volání) zpracovává pouze jednu zprávu v daném okamžiku (obdobná `ConcurencyMode.Single`). K zajištění bezpečnosti vlákna, uzamkne Windows Communication Foundation (WCF) `InstanceContext` zpracovává zprávu tak, aby zpracovat žádné další zprávy. V případě vícenásobné režim `InstanceContext` odemknut těsně před plánovaným začátkem služby umožňuje odchozí volání a tím umožní následných volání (může to být vícenásobné, jak je uvedeno v ukázce) se získat zámek příště je k dispozici ve službě. Abychom si předvedli chování, tato ukázka vysvětluje, jak může klient a služba odesílání zpráv mezi sebou pomocí duplexního kontraktu.  
  
 Duplexní kontrakt s je kontrakt definovaný `Ping` implementování službou a metoda zpětného volání metody `Pong` implementování klientem. Klient vyvolá serveru `Ping` metodu s čárka počítat, a tím inicializace volání. Služba zkontroluje, zda počet impulsů není roven 0 a poté vyvolá tak potřebná zpětná volání `Pong` metoda při dekrementace počtu impulsů. To se provádí v následujícím kódu v ukázce.  
  
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
  
 Při zpětném volání `Pong` implementace má stejnou logikou jako `Ping` implementace. To znamená, zkontroluje, zda počet impulsů není nula a potom vyvolá `Ping` metoda zpětného volání kanálu (v tomto případě je kanál, který jste použili k zaslání původní `Ping` zpráva) pomocí značek počet sníží o 1. V okamžiku, kdy počet impulsů dosáhne hodnoty 0, vrátí tato metoda hodnotu a rozbalení všechny odpovědi zpátky na první volání, která iniciovala volání klienta. To je ukázáno v implementaci zpětného volání.  
  
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
  
 Jak `Ping` a `Pong` metody jsou požadavku/odpovědi, což znamená, že první volání `Ping` nevrací až do volání `CallbackChannel<T>.Pong()` vrátí. V klientském počítači `Pong` metoda nemůže vrátit až do další `Ping` volání, že ji nastavit na vrátí. Protože zpětné volání a služba musí volat odchozí požadavek/odpověď předtím, než můžete odpovědět čekající žádosti, musí být obě implementace označeny ConcurrencyMode.Reentrant chování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstruje  
 Ke spuštění ukázky, sestavení projektů klientem a serverem. Pak otevřete dvě okně příkazového řádku a přejděte do adresáře \<ukázka > \CS\Service\bin\debug a \<ukázka > \CS\Client\bin\debug adresáře. Potom spusťte služby zadáním `service.exe` a pak vyvolejte Client.exe s počáteční hodnotou ticks předaný jako vstupní argument. Ukázkový výstup pro 10 impulzech se zobrazí.  
  
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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Viz také:
