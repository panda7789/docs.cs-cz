---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 24bb9b483a3f26241f895d68b763a1974b02151b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716443"
---
# <a name="expected-exceptions"></a>Očekávané výjimky
Tato ukázka předvádí, jak zachytit očekávané výjimky při použití typového klienta. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky. V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tento příklad znázorňuje zachycení a zpracování dvou očekávaných typů výjimek, které musí zpracovat správné programy: `TimeoutException` a `CommunicationException`.  
  
 Výjimky, které jsou vyvolány ze způsobů komunikace u klienta služby Windows Communication Foundation (WCF), jsou buď očekávány, nebo neočekávané. Neočekávané výjimky zahrnují závažná selhání jako `OutOfMemoryException` a chyby programování, jako je `ArgumentNullException` nebo `InvalidOperationException`. Obvykle neexistuje žádný užitečný způsob, jak zpracovat neočekávané chyby, takže byste je neměli zachytit při volání metody komunikace klienta WCF.  
  
 Očekávané výjimky z metod komunikace na klientovi WCF zahrnují `TimeoutException`, `CommunicationException`a jakoukoliv odvozenou třídu `CommunicationException`. Ty naznačují problém během komunikace, který je možné bezpečně zpracovat přerušením klienta WCF a odesláním chyby komunikace. Vzhledem k tomu, že externí faktory mohou způsobovat tyto chyby v jakékoli aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit ji, když k nim dojde.  
  
 Existuje několik odvozených tříd `CommunicationException`, které může klient vyvolat. V některých případech aplikace také zachytit některé z nich, aby provedly speciální zpracování, ale ostatní se budou zpracovávat jako `CommunicationException`. To lze provést tak, že nejprve zachytíte konkrétnější typ výjimky a potom zachytíte `CommunicationException` v pozdější klauzuli catch.  
  
 Kód, který volá metodu komunikace klienta, musí zachytit `TimeoutException` a `CommunicationException`. Jedním ze způsobů, jak tyto chyby zpracovat, je přerušit klienta a ohlásit selhání komunikace.  
  
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
  
 Pokud dojde k očekávané výjimce, klient může nebo nemusí být použitelný později. Chcete-li zjistit, zda je klient stále použitelný, zkontrolujte, zda je vlastnost `State` `CommunicationState`. Otevřít. Pokud je stále otevřený, je stále možné ho použít. V opačném případě byste měli klienta přerušit a uvolnit všechny odkazy na něj.  
  
> [!CAUTION]
> Můžete se setkat s tím, že klienti, kteří mají relaci, již nejsou po výjimce použitelné, a klienti, kteří relaci nemají, jsou často i nadále použitelné i po výjimce. Ani jedna z těchto možností není zaručena, takže pokud se chcete pokusit nadále používat klienta po výjimce, měla by aplikace zkontrolovat vlastnost `State` a ověřit, zda je klient stále otevřen.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí odezvy operace a výjimky.  
  
 Proces klienta spouští dva scénáře, z nichž každý se pokusí zavolat `Add` následovaný `Divide`. První scénář simuluje problém se sítí tím, že před provedením volání `Divide`přerušil klienta. Druhý scénář způsobí vypršení časového limitu tím, že nastaví časový limit příliš krátký pro dokončení metody. Očekávaný výstup z klientského procesu je:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
