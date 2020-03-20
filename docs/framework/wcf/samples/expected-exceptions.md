---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144706"
---
# <a name="expected-exceptions"></a>Očekávané výjimky
Tato ukázka ukazuje, jak zachytit očekávané výjimky při použití zadaného klienta. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka ukazuje zachycení a zpracování dvou očekávaných `TimeoutException` typů `CommunicationException`výjimek, které správné programy musí zpracovat: a .  
  
 Výjimky, které jsou vyvolány z komunikačních metod v klientovi WCF (Windows Communication Foundation) jsou očekávané nebo neočekávané. Neočekávané výjimky zahrnují `OutOfMemoryException` katastrofická selhání, jako jsou chyby programování, jako je `ArgumentNullException` nebo `InvalidOperationException`. Obvykle neexistuje žádný užitečný způsob zpracování neočekávaných chyb, takže obvykle byste je neměli zachytit při volání metody komunikace klienta WCF.  
  
 Očekávané výjimky z komunikačních metod `TimeoutException`na `CommunicationException`wcf klienta `CommunicationException`patří , a všechny odvozené třídy . Ty označují problém během komunikace, které lze bezpečně zpracovat přerušením wcf klienta a hlášení selhání komunikace. Vzhledem k tomu, že externí faktory mohou způsobit tyto chyby v libovolné aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit, když k nim dojde.  
  
 Existuje několik odvozených `CommunicationException` tříd, které může klient vyvolat. V některých případech aplikace také chytit některé z nich udělat zvláštní `CommunicationException`zacházení, ale nechte ostatní zacházet jako . Toho lze dosáhnout zachycením konkrétnější typ výjimky `CommunicationException` první a potom zachycení v pozdější catch klauzule.  
  
 Kód, který volá metodu `TimeoutException` komunikace `CommunicationException`klienta, musí zachytit a . Jedním ze způsobů, jak tyto chyby zpracovat, je přerušit klienta a nahlásit selhání komunikace.  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 Pokud dojde k očekávané výjimce, klient může nebo nemusí být použitelný později. Chcete-li zjistit, zda je klient `State` stále `CommunicationState`použitelný, zkontrolujte, zda je vlastnost . Otevřít. Pokud je stále otevřen, je stále použitelný. V opačném případě byste měli přerušit klienta a uvolnit všechny odkazy na něj.  
  
> [!CAUTION]
> Můžete pozorovat, že klienti, kteří mají relaci jsou často již nelze použít po výjimce a klienti, kteří nemají relaci jsou často stále použitelné po výjimce. Ani jeden z nich však není zaručena, takže pokud chcete pokračovat v používání `State` klienta po výjimce aplikace by měla zkontrolovat vlastnost ověřit klient je stále otevřen.  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny odpovědi na operaci a výjimky.  
  
 Proces klienta spustí dva scénáře, z `Add` nichž `Divide`každý se pokusí volat následovaný . První scénář simuluje problém sítě přerušením klienta `Divide`před provedením volání . Druhý scénář způsobí, že podmínka časového limitu nastavením časový limit příliš krátký pro dokončení metody. Očekávaný výstup z klientského procesu je:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
