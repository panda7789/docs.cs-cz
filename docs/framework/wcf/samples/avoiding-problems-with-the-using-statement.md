---
title: Jak se vyhnout problémům s příkazem Using
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a>Jak se vyhnout problémům s příkazem Using
Tento příklad znázorňuje, jak byste neměli používat "použití" příkaz automaticky vyčištění prostředků při použití typový klient jazyka C#. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tento příklad ukazuje dva běžné problémy, ke kterým dochází při používání "použití" příkaz s typem klienty, stejně jako kód, který správně vyčistí po výjimky jazyka C#.  
  
 "Pomocí" příkazu jazyka C# výsledkem volání `Dispose`(). Je to stejné nastavení jako `Close`(), který může vyvolat výjimky, když dojde k chybě sítě. Protože volání `Dispose`() odehrává implicitně se na pravé složené závorce bloku "použití", tento zdroj výjimek je pravděpodobně přejdete unnoticed i uživatelé psaní kódu a čtení kódu. To představuje potenciální zdroj chyby aplikace.  
  
 První problém, zobrazené `DemonstrateProblemUsingCanThrow` metodou, je, že pravé složené závorce výjimku a kód po pravé složené závorce nepracuje:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 I v případě, že nic uvnitř použití blokovat vyvolá výjimku nebo uvnitř použití všechny výjimky jsou zachyceny bloku, `Console.Writeline` nemusí dojít, protože implicitní `Dispose`volání () na pravé složené závorce může vyvolat výjimku.  
  
 Druhý problém, zobrazené `DemonstrateProblemUsingCanThrowAndMask` metodou, je jiná vyplývá pravé složené závorce došlo k výjimce:  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Protože `Dispose`() se provádí v bloku "finally" `ApplicationException` je nikdy neuvidí mimo použití blokování, pokud `Dispose`() se nezdaří. Pokud kód mimo musí vědět o tom, kdy `ApplicationException` dojde, "pomocí" konstrukce může způsobit problémy s nástrojem maskování výjimku.  
  
 Nakonec ukazuje, jak vyčistit správně při výskytu výjimek v ukázce `DemonstrateCleanupWithExceptions`. Tato služba využívá bloku try/catch k hlášení chyb a volání `Abort`. Najdete v článku [očekává výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) ukázku další podrobnosti o zachytávání výjimek z volání klienta.  
  
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
>  Pomocí příkazu a ServiceHost: mnoho samoobslužné hostování aplikací trochu více než hostování služby a ServiceHost.Close zřídka vyvolá výjimku, abyste takové aplikace můžete bezpečně používat na pomocí příkaz s hostiteli služby. Upozorňujeme však, že můžete vyvolat ServiceHost.Close `CommunicationException`, takže pokud vaše aplikace bude pokračovat po zavření ServiceHost, neměli byste na pomocí prohlášení a postupujte podle vzoru dříve zadané.  
  
 Když spustíte ukázku, zobrazí se v okně konzoly klienta odpovědí na operaci a výjimky.  
  
 Klient proces spouští tři scénáře, každý z které pokusy o volání `Divide`. První scénář ukazuje kód přeskočeno z důvodu výjimku z `Dispose`(). Druhý scénář ukazuje výjimku důležité maskovaného kvůli výjimku z `Dispose`(). Třetí scénář ukazuje správné vyčištění.  
  
 Je očekávaný výstup z procesu klienta:  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Viz také
