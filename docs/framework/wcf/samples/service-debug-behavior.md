---
title: Chování ladění služby
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: d84f3281beee78f8328011026e4d4653c05ed849
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574895"
---
# <a name="service-debug-behavior"></a>Chování ladění služby
Tato ukázka předvádí, jak lze konfigurovat nastavení chování ladění služby. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru. To je možné provést imperativně v kódu.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Soubor Web.config pro server se definuje chování ladění služby povolit stránku nápovědy a zpracování výjimek, jak je znázorněno v následujícím příkladu.  
  
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
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) je prvek konfigurace, který umožňuje změnit vlastnosti chování ladění služby. Uživatel může upravit toto chování a dosáhnout následující:  
  
-   To umožňuje službě vrátit jakoukoliv výjimku, která je vyvolána kódem aplikace, i v případě, že výjimka není deklarován pomocí <xref:System.ServiceModel.FaultContractAttribute>. To se provádí nastavením `includeExceptionDetailInFaults` k `true`. Toto nastavení je užitečné při ladění v případech, kde je serveru vyvolání neočekávané výjimky.  
  
    > [!IMPORTANT]
    >  Není bezpečné zapnout toto nastavení v produkčním prostředí. Server neočekávané výjimky může mít některé informace, která není určená pro klienta a proto nastavení `includeExceptionDetailsInFaults` k `true` může vést úniku informací.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) také umožňuje uživatelům povolit nebo zakázat na stránce nápovědy. Každá služba Volitelně můžete zveřejnit stránce nápovědy, který obsahuje informace o službě včetně koncový bod pro získání WSDL pro službu. To se dá nastavit tak, že nastavíte `httpHelpPageEnabled` k `true`. To umožňuje na stránce nápovědy, který se má vrátit požadavek GET na základní adresu služby. Tuto adresu můžete změnit nastavením jiný atribut `httpHelpPageUrl`. Lze zvýšit tím zabezpečení pomocí protokolu HTTPS místo protokolu HTTP. To můžete udělat tak, že nastavíte `httpsHelpPageEnabled` a `httpsHelpPageUrl`.  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. První tři operace (přidání, odečíst a násobení) musí být úspěšný. Poslední operace ("dělení") se nezdaří s dělení nulovou výjimky.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Viz také:
