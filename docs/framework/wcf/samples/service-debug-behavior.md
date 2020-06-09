---
title: Chování ladění služby
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 53f21129860c644d09d1a2eb9cb956aecf8ab0ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596635"
---
# <a name="service-debug-behavior"></a>Chování ladění služby

Tato ukázka předvádí, jak lze nakonfigurovat nastavení chování ladění služby. Ukázka je založena na [Začínáme](getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru. Může být také provedeno imperativně v kódu.

V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Soubor Web. config pro Server definuje chování ladění služby, aby bylo možné povolit stránku a zpracování výjimek stránky s nápovědu, jak je znázorněno v následující ukázce.

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

[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)je prvek konfigurace, který umožňuje změnit vlastnosti chování ladění služby. Uživatel může toto chování změnit, aby bylo možné provést následující akce:

- To umožňuje službě vracet všechny výjimky, které jsou vyvolány kódem aplikace, i v případě, že výjimka není deklarována pomocí <xref:System.ServiceModel.FaultContractAttribute> . Je prováděna nastavením `includeExceptionDetailInFaults` na `true` . Toto nastavení je užitečné při ladění případů, kdy server vyvolává neočekávanou výjimku.

  > [!IMPORTANT]
  > Toto nastavení v produkčním prostředí není bezpečné zapnout. Neočekávaná výjimka serveru může obsahovat některé informace, které nejsou určené pro klienta, a nastavení, `includeExceptionDetailsInFaults` které `true` by mohlo vést k úniku informací.

- [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Také umožňuje uživateli povolit nebo zakázat stránku s usnadněním. Každá služba může volitelně vystavit stránku s nápovědu obsahující informace o službě, včetně koncového bodu pro získání WSDL pro službu. To lze povolit nastavením `httpHelpPageEnabled` na `true` . Tím umožníte, aby se stránka s Nápověda vrátila do žádosti o získání základní adresy služby. Tuto adresu můžete změnit nastavením jiného atributu `httpHelpPageUrl` . Toto zabezpečení můžete provést pomocí protokolu HTTPS místo HTTP. To se dá udělat nastavením `httpsHelpPageEnabled` a `httpsHelpPageUrl` .

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. První tři operace (sčítání, odečítání a násobení) musí být úspěšné. Poslední operace ("dělení") se nezdařila s oddělenou výjimkou dělení nulou.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
