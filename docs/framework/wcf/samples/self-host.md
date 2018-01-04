---
title: "Vlastní hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b662c034e4c3d7c21c9a48537cd7f80f4bb6b659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="self-host"></a>Vlastní hostování
Tento příklad ukazuje, jak implementovat samoobslužné hostovanou službu v konzolové aplikaci. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Konfigurační soubor služby má byl přejmenován ze souboru Web.config na App.config a upravit tak, aby konfigurace základní adresu, která hostitel používá. Zdrojový kód služby se změnilo implementovat statického `Main` funkce, která vytvoří a otevře poskytující základní adresu nakonfigurované hostitele služby. Implementace služby se změnilo zapisovat výstup do konzoly pro každou operaci. Klient byl beze změny, s výjimkou konfigurace adresa správná koncového bodu služby.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka implementuje statické hlavní funkce, která se vytvořit <xref:System.ServiceModel.ServiceHost> pro v dané `CalculatorService` zadejte, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 Pokud služba je hostovaná v Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS), je základní adresa služby poskytované hostitelské prostředí. V případě vlastním hostováním zadejte základní adresu sami. To se provádí pomocí `add` element, podřízená položka [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podřízeným [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podřízeným [ \<služby > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak je předvedeno v následující ukázka konfigurace.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
