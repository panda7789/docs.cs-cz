---
title: "Očekávané výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ddddd51229712f85bc780889169e159c1c83e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expected-exceptions"></a>Očekávané výjimky
Tento příklad znázorňuje, jak zachytit očekávané výjimky při použití typový klient. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tento příklad znázorňuje zachytávání a zpracování těchto dvou typů očekávané výjimky, které opravit programy musí zpracovat: `TimeoutException` a `CommunicationException`.  
  
 Výjimky, které jsou vyvolány z metody komunikace na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta jsou očekávané nebo neočekávané. Neočekávané výjimky patří závažné chyby jako `OutOfMemoryException` a programovací chyby, jako jsou `ArgumentNullException` nebo `InvalidOperationException`. Obvykle se nedá nijak užitečné pro zpracování neočekávaným chybám, takže obvykle neměli je zachytit při volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metoda komunikace s klientem.  
  
 Na očekávané výjimky z metody komunikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnují klienta `TimeoutException`, `CommunicationException`, a všechny odvozené třídy `CommunicationException`. Ty naznačují problém při komunikaci, která může bezpečně ošetřit přerušení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a vytváření sestav selhání komunikace. Vzhledem k tomu, že externí faktory mohou způsobit tyto chyby v jakékoli aplikaci, musíte správné aplikace zachytit tyto výjimky a obnovit, pokud k nim dojde.  
  
 Existuje několik odvozené třídy `CommunicationException` který lze vyvolat klienta. V některých případech aplikace i catch některé z těchto provést zvláštní zpracování, ale nechat řešeny jako ostatní `CommunicationException`. To lze provést tak, že nejprve zachytávání konkrétnější typ výjimky a potom zachytávání `CommunicationException` novější klauzule catch.  
  
 Kód, který volá metodu komunikace klienta musí catch `TimeoutException` a `CommunicationException`. Jedním ze způsobů ke zpracování těchto chyb je abort klienta a ohlásí selhání komunikace.  
  
```  
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
  
 Pokud dojde k výjimce očekávané, klienta může nebo nemusí být použitelná později. Pokud chcete zjistit, pokud je klient stále možné použít, zkontrolujte, zda `State` vlastnost je `CommunicationState`. Otevřít. Pokud je stále otevřen, je stále možné použít. V opačném případě by měl abort klienta a uvolnit všechny odkazy na ni.  
  
> [!CAUTION]
>  Můžete pozorovat, že klienti, kteří mají relaci často již nejsou použitelné po výjimce a klientů, které nemají relaci jsou stále často použitelné po výjimce. Však ani jedno z těchto záruku, že, takže pokud chcete pokračovat i po výjimce vaše aplikace by se mělo zjistit pomocí klienta `State` vlastnost ověření klienta je stále otevřen.  
  
 Když spustíte ukázku, zobrazí se v okně konzoly klienta odpovědí na operaci a výjimky.  
  
 Spustí proces klienta dva scénáře, každý z které pokusy o volání `Add` následuje `Divide`. První scénář simuluje potíže se sítí pomocí přerušení klient před provedením volání `Divide`. Druhý scénář způsobí, že podmínka časový limit nastavením časový limit příliš krátká pro metodu dokončení. Je očekávaný výstup z procesu klienta:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a>Viz také
