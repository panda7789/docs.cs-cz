---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 963606f4cfd34acb1c4400324cdbb318e3186103
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039701"
---
# <a name="expected-exceptions"></a>Očekávané výjimky
Tato ukázka předvádí, jak zachytit očekávané výjimky při použití typového klienta. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky. V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tento příklad znázorňuje zachycení a zpracování dvou očekávaných typů výjimek, které musí zpracovat správné programy: `TimeoutException` a `CommunicationException`.  
  
 Výjimky, které jsou vyvolány ze způsobů komunikace u klienta služby Windows Communication Foundation (WCF), jsou buď očekávány, nebo neočekávané. Neočekávané výjimky zahrnují závažná `OutOfMemoryException` selhání jako a chyby `ArgumentNullException` programování `InvalidOperationException`jako nebo. Obvykle neexistuje žádný užitečný způsob, jak zpracovat neočekávané chyby, takže byste je neměli zachytit při volání metody komunikace klienta WCF.  
  
 Očekávané výjimky ze způsobů komunikace na klientovi WCF zahrnují `TimeoutException`, `CommunicationException` `CommunicationException`a jakékoliv odvozené třídy. Ty naznačují problém během komunikace, který je možné bezpečně zpracovat přerušením klienta WCF a odesláním chyby komunikace. Vzhledem k tomu, že externí faktory mohou způsobovat tyto chyby v jakékoli aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit ji, když k nim dojde.  
  
 Existuje několik odvozených tříd `CommunicationException` , které může klient vyvolat. V některých případech aplikace také zachytit některé z nich, aby provedla speciální zpracování, ale ostatní budou zpracována jako `CommunicationException`. To lze provést tak, že nejprve zachytíte konkrétnější typ výjimky a pak zachytíte `CommunicationException` v pozdější klauzuli catch.  
  
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
  
 Pokud dojde k očekávané výjimce, klient může nebo nemusí být použitelný později. Chcete-li zjistit, zda je klient stále použitelný, zkontrolujte `State` , zda `CommunicationState`je vlastnost nastavena na hodnotu. Otevřít. Pokud je stále otevřený, je stále možné ho použít. V opačném případě byste měli klienta přerušit a uvolnit všechny odkazy na něj.  
  
> [!CAUTION]
> Můžete se setkat s tím, že klienti, kteří mají relaci, již nejsou po výjimce použitelné, a klienti, kteří relaci nemají, jsou často i nadále použitelné i po výjimce. Ani jedna z těchto možností není zaručena, takže pokud se chcete pokusit nadále používat klienta po výjimce, měla by aplikace zkontrolovat `State` vlastnost a ověřit, zda je klient stále otevřen.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí odezvy operace a výjimky.  
  
 Proces klienta spouští dva scénáře, z nichž každý se pokusí zavolat `Add` `Divide`za ním. První scénář simuluje problém se sítí přerušením klienta před uskutečněním volání `Divide`. Druhý scénář způsobí vypršení časového limitu tím, že nastaví časový limit příliš krátký pro dokončení metody. Očekávaný výstup z klientského procesu je:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
