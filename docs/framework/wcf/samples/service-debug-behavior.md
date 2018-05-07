---
title: Chování ladění služby
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 5edbf640fbda72599b5d14ce482ae186e91681c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-debug-behavior"></a>Chování ladění služby
Tento příklad znázorňuje, jak lze nakonfigurovat nastavení chování ladění služby. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru. Je možné také ji provést imperativní v kódu.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Soubor Web.config pro server definuje chování ladění služby povolit stránku nápovědy a výjimek, jak znázorňuje následující ukázka.  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) je konfigurace elementu, který umožňuje změnit vlastnosti chování ladění služby. Uživatele můžete upravit toto chování cíle jsou následující:  
  
-   To umožňuje službě vrátit jakékoli výjimky vyvolané kódem aplikace i v případě, že výjimka není deklarovaný pomocí <xref:System.ServiceModel.FaultContractAttribute>. Se provádí nastavením `includeExceptionDetailInFaults` k `true`. Toto nastavení je užitečné při ladění případech, kde je serveru došlo k neočekávané výjimce.  
  
    > [!IMPORTANT]
    >  Není zabezpečený zapnout toto nastavení v produkčním prostředí. Výjimku neočekávané server může mít některé informace, která není určená pro klienta a tak nastavení `includeExceptionDetailsInFaults` k `true` může vést k tomu dojde k úniku informací.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) také umožňuje uživatelům povolit nebo zakázat tuto stránku nápovědy. Každé služby můžete volitelně vystavit stránku nápovědy, která obsahuje informace o službě včetně koncový bod získat WSDL pro službu. To se dá nastavit nastavením `httpHelpPageEnabled` k `true`. To umožňuje stránku nápovědy a vrátit požadavek GET na adresu základní služby. Tuto adresu můžete změnit nastavením jiný atribut `httpHelpPageUrl`. Můžete nastavit to zabezpečené pomocí protokolu HTTPS místo protokolu HTTP. To můžete provést nastavením `httpsHelpPageEnabled` a `httpsHelpPageUrl`.  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. První tři operace (přidání, odečtena a násobení) musí být úspěšné. Poslední operace ("Rozděl") se nezdaří s dělení nulové výjimkou.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Viz také
