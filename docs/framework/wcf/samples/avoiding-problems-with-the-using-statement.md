---
title: Jak se vyhnout problémům s příkazem Using
ms.date: 03/30/2017
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 2c7534a56b2cc8fdc674242e135d70bec7f5017a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394695"
---
# <a name="avoiding-problems-with-the-using-statement"></a>Jak se vyhnout problémům s příkazem Using
Tato ukázka předvádí, jak byste neměli používat "" příkaz using automaticky vyčistit prostředky, při použití typový klient C#. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad ukazuje dvě běžné problémy, ke kterým dochází při použití jazyka C# "" příkaz s typem klienty, stejně jako kód, který správně vyčištění po výjimkách.  
  
 Příkaz "using" C# výsledkem volání `Dispose`(). To je stejný jako `Close`(), což může vyvolat výjimky, když dojde k chybě sítě. Protože volání `Dispose`() se implicitně odehrává na pravou složenou závorku "pomocí" bloku, tento zdroj výjimky je pravděpodobně přejít unnoticed i uživatelé psaní kódu a čtení kódu. Reprezentuje možným zdrojem chyby aplikace.  
  
 Prvním problémem, ukazuje `DemonstrateProblemUsingCanThrow` metoda, je, že pravou složenou závorku výjimku a kód po pravé složené závorce nespustí:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 I když nic uvnitř using blokovat útoky DoS vyvolá výjimku nebo uvnitř using všechny výjimky jsou zachyceny bloku, `Console.Writeline` nemusí dojít, protože implicitní `Dispose`volání () na pravé složené závorce může vyvolat výjimku.  
  
 Druhý problém ukazuje `DemonstrateProblemUsingCanThrowAndMask` metoda, je jiný nepřímo pravou složenou závorku, došlo k výjimce:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Protože `Dispose`() nastane uvnitř bloku "klíčové slovo finally" `ApplicationException` nikdy se neprohlédlo mimo using blokovat, pokud `Dispose`() se nezdaří. Pokud kód mimo musí vědět o tom, kdy `ApplicationException` dojde, "using" konstruktoru může způsobit problémy pomocí jejich maskování této výjimky.  
  
 Nakonec vzorek ukazuje, jak vyčistit správně při výskytu výjimek v `DemonstrateCleanupWithExceptions`. Tento mechanismus využívá bloku try/catch k nahlášení chyb a volání `Abort`. Zobrazit [očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázka podrobné informace o zachycení výjimky z volání klienta.  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  Pomocí příkazu a hostitel služby: mnoho samoobslužné hostování aplikací trochu více než hostování služby a ServiceHost.Close zřídka vyvolá výjimku, takže tyto aplikace můžete bezpečně použít na pomocí příkazu s hostitele ServiceHost. Však být vědomi, že může vyvolat ServiceHost.Close `CommunicationException`, takže pokud vaše aplikace bude pokračovat až po zavření hostitele ServiceHost, měli byste se vyhnout pomocí příkazu a postupujte podle vzoru předem.  
  
 Při spuštění ukázky operace odpovědi a výjimky jsou zobrazeny v okně konzoly klienta.  
  
 Klient proces spouští tři scénáře, každý z které pokusy o volání `Divide`. První scénář ukazuje kód přeskočeno z důvodu výjimky z `Dispose`(). Druhý scénář ukazuje důležité výjimku z důvodu výjimky z maskovaného `Dispose`(). Třetí scénář ukazuje správné vyčištění.  
  
 Očekávaný výstup z procesu klienta je:  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Viz také
