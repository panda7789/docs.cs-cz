---
title: Použití metod Close a Abort k uvolnění prostředků klienta WCF
description: Dispose může selhat a vyvolat výjimky, pokud dojde k selhání sítě. To může způsobit nežádoucí chování. Místo toho použijte příkaz Zavřít a přerušit k uvolnění prostředků klienta, pokud se síť nezdařila.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 38861252a470f71a6fa88554e289344e2918d710
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715324"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>V případě, že jsou síťová připojení vyřazena, uzavřete a přerušit uvolnění prostředků

Tato ukázka demonstruje použití metod `Close` a `Abort` k vyčištění prostředků při použití typového klienta. Příkaz `using` způsobuje výjimky v případě nerobustního síťového připojení. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky. V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Tato ukázka ukazuje dva běžné problémy, ke kterým dochází při použití příkazu C# "using" se zadanými klienty, jakož i kódu, který správně čistí po výjimkách.

C# Příkaz using má za následek volání `Dispose`(). To je stejné jako `Close`(), což může vyvolat výjimky při výskytu chyby sítě. Vzhledem k tomu, že volání `Dispose`() probíhá implicitně na pravé závorce bloku "using", tento zdroj výjimek je pravděpodobně neupozorněn na uživatele, kteří píší kód a čtou kód. To představuje potenciální zdroj chyb aplikace.

První problém, znázorněný v metodě `DemonstrateProblemUsingCanThrow`, je, že pravá složená závorka vyvolá výjimku a kód po pravé složené závorce nespustí:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

I v případě, že nic uvnitř bloku using vyvolá výjimku nebo jsou zachyceny všechny výjimky uvnitř bloku using, `Console.WriteLine` pravděpodobně neproběhne, protože volání implicitního `Dispose`() na pravé závorce může vyvolat výjimku.

Druhý problém, znázorněný v metodě `DemonstrateProblemUsingCanThrowAndMask`, je další příčinou pravé složené závorky, která vyvolává výjimku:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

Vzhledem k tomu, že se `Dispose`() nachází uvnitř bloku "finally", `ApplicationException` se nikdy nezobrazuje vně bloku using, pokud `Dispose`() dojde k chybě. Pokud kód mimo musí znát, kdy k `ApplicationException` dojde, může konstrukce "using" způsobit problémy pomocí maskování této výjimky.

Nakonec Ukázka ukazuje, jak správně vyčistit při výskytu výjimek v `DemonstrateCleanupWithExceptions`. K nahlášení chyb a volání `Abort`se používá blok try/catch. Další podrobnosti o zachycování výjimek od klientských volání najdete v ukázce [očekávaných výjimek](../../../../docs/framework/wcf/samples/expected-exceptions.md) .

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
> Příkaz using a Třída ServiceHost: mnoho aplikací pro samoobslužné hostování má málo větší počet než hostitel a služba a třídu ServiceHost. zavření zřídka vyvolá výjimku, takže takové aplikace mohou bezpečně používat příkaz using s použitím třídy ServiceHost. Upozorňujeme však, že Třída ServiceHost. Close může vyvolat `CommunicationException`, takže pokud vaše aplikace po zavření hostitele ServiceHost pokračuje, měli byste se vyhnout příkazu Using a postupovat podle výše uvedeného vzoru.

Při spuštění ukázky se v okně konzoly klienta zobrazí odezvy operace a výjimky.

Proces klienta spouští tři scénáře, z nichž každý se pokusí volat `Divide`. První scénář ukazuje přeskočení kódu z důvodu výjimky z `Dispose`(). Druhý scénář ukazuje, že důležitá výjimka je maskována z důvodu výjimky z `Dispose`(). Třetí scénář demonstruje správné vyčištění.

Očekávaný výstup z klientského procesu je:

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
