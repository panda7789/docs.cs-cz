---
title: Očekávané výjimky
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 3add9faa9a07249639c1ff3e83469d0634008472
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990194"
---
# <a name="expected-exceptions"></a>Očekávané výjimky
Tento příklad ukazuje, jak zachytit očekávané výjimky, při použití typu klienta. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka předvádí, zachycení a zpracování dva typy očekávané výjimky, které opravte programy musí zpracovat: `TimeoutException` a `CommunicationException`.  
  
 Výjimky, které jsou vyvolány z metody komunikace klienta Windows Communication Foundation (WCF) jsou očekávané nebo neočekávané. Neočekávané výjimky zahrnují katastrofických selhání jako `OutOfMemoryException` a programové chyby, jako jsou `ArgumentNullException` nebo `InvalidOperationException`. Obvykle se nedají užitečné pro zpracování neočekávaných chyb, takže obvykle že při volání metody komunikace klienta WCF, neměli byste je zachytit.  
  
 Očekávané výjimky z metody komunikace na klienta WCF zahrnují `TimeoutException`, `CommunicationException`, a všechny odvozené třídy `CommunicationException`. Ty naznačují problém při komunikaci, která může bezpečně ošetřit přerušení klienta WCF a hlášení selhání komunikace. Protože vnější faktory mohou způsobit tyto chyby v jakékoli aplikaci, správné aplikace musí zachytit tyto výjimky a obnovit, když k nim dojde.  
  
 Existuje několik odvozené třídy `CommunicationException` , který může klient vyvolat. V některých případech může aplikace také catch některé z nich proveďte zvláštní zpracování, ale umožněte ostatním zacházet jako `CommunicationException`. To můžete udělat nejdřív zachytávání konkrétnější typ výjimky a následné zachycování `CommunicationException` v pozdější klauzule catch.  
  
 Musíte zachytit kód, který volá metodu komunikaci klienta `TimeoutException` a `CommunicationException`. Jedním ze způsobů zpracování těchto chyb je přerušit klienta a tvorba sestav selhání komunikace.  
  
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
  
 Pokud dojde k očekávané výjimky, klient může nebo nemusí být použitelné později. Pokud chcete zjistit, pokud je klient stále možné použít, zkontrolujte, že `State` vlastnost `CommunicationState`. Otevřít. Pokud je stále otevřen, je stále možné použít. V opačném případě by měl přerušení klienta a uvolnit všechny odkazy na ni.  
  
> [!CAUTION]
>  Podívat se, že klienti, kteří mají relaci často již nejsou použitelné po výjimce a klienti, které nemají relaci stále často použitelné po výjimce. Ale ani jeden z nich je zaručeno, tak pokud budete chtít pokračovat i po výjimce by měla vaše aplikace provádět pomocí klienta `State` vlastnost ověření klienta je stále otevřen.  
  
 Při spuštění ukázky operace odpovědi a výjimky jsou zobrazeny v okně konzoly klienta.  
  
 Spustí proces klienta dva scénáře, každý z které pokusy o volání `Add` následovaný `Divide`. První scénář simuluje potíže se sítí přerušením klient před provedením volání `Divide`. Druhý scénář způsobí, že vypršení časového limitu podmínku tak, že nastavíte časový limit příliš krátká pro metodu k dokončení. Očekávaný výstup z procesu klienta je:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
