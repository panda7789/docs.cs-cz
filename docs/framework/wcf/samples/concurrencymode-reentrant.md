---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: d0ecd4b0c39c6a736a176a61490f454c2bab2e20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502641"
---
# <a name="concurrencymode-reentrant"></a>ConcurrencyMode Reentrant
Tento příklad znázorňuje nezbytné a důsledky použití ConcurrencyMode.Reentrant na implementaci služby. ConcurrencyMode.Reentrant znamená, že služba (nebo zpětného volání) zpracovává jenom jednu zprávu v daném okamžiku (podobá `ConcurencyMode.Single`). K zajištění bezpečnosti přístup z více vláken, zamkne Windows Communication Foundation (WCF) `InstanceContext` zpracování zprávy, takže lze zpracovat žádné další zprávy. V případě vícenásobné režimu `InstanceContext` je odemčený těsně před služby umožňuje odchozí volání následných volání (může to být vícenásobné, jak je předvedeno v ukázce) a tím umožní získat zámek příštím pochází službě. K předvedení chování, příklad ukazuje, jak může klient a služba odesílání zpráv mezi sebou pomocí duplexního kontraktu.  
  
 Kontrakt definovaný je duplexního kontraktu s `Ping` metoda se implementuje službou a metoda zpětného volání `Pong` se implementuje klientem. Klient vyvolá serveru `Ping` metoda s osové počet a inicializaci volání. Služba zkontroluje, zda počet značek není roven 0 a poté vyvolá zpětná volání `Pong` metoda při dekrementace počet značek. K tomu je potřeba následující kód v ukázce.  
  
```  
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
  
 Při zpětném volání `Pong` implementace má stejné logiky, která jako `Ping` implementace. To znamená, se ověří, zda počet značek není nula a poté vyvolá `Ping` metoda zpětného volání kanálu (v takovém případě je kanál, který se používá k odesílání původní `Ping` zpráva) s značek počet odečte o 1. Okamžiku, kdy počet značek dosáhne 0, vrátí tato metoda hodnotu a rozbalování všechny odpovědi zpět na první volání klienta, která iniciovala volání. Ta se zobrazí v implementaci zpětného volání.  
  
```  
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
  
 Jak `Ping` a `Pong` jsou požadavek nebo odpověď, což znamená, že první volání metody `Ping` nevrací dokud volání `CallbackChannel<T>.Pong()` vrátí. Na straně klienta `Pong` metoda nemůže vrátit až do dalšího `Ping` volání, aby se provedené vrátí. Vzhledem k tomu odchozí volání požadavek nebo odpověď musí provádět zpětné volání a služby, než může odpovědět čekající žádosti, musí být obě implementace označen s chováním ConcurrencyMode.Reentrant.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstruje  
 Do spuštění vzorového sestavení projektů klienta a serveru. Dále otevřete dvě příkaz windows a přejděte do adresáře \<ukázka > \CS\Service\bin\debug a \<ukázka > \CS\Client\bin\debug adresáře. Potom spusťte službu zadáním `service.exe` a pak vyvolejte Client.exe s počáteční hodnotou ticks předat jako vstupní argument. Ukázkový výstup pro rysky 10 se zobrazí.  
  
```  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Viz také
