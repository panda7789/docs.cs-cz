---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1a236f1812d3124e83702a97e1877b7fec10be64
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715494"
---
# <a name="configuration-channel-factory"></a>Postup konfiguračního kanálu
Tato ukázka pokrývá použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje centrální správu konfigurace klienta WCF. To může být užitečné také ve scénářích, kdy je konfigurace vybrána nebo změněna po dobu načtení domény aplikace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Účely
 V této ukázce se dozvíte, jak pomocí <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli použít výchozí konfigurační soubor aplikace.

 Vzorek se skládá ze dvou projektů. Prvním projektem je jednoduchá služba, která se používá k odpovědi na zprávy přicházející od klientů. Druhý projekt je klientská aplikace, která vytváří dva <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objekty pomocí <xref:System.Configuration.ExeConfigurationFileMap> pro konfigurační soubor test. config a používá je ke komunikaci se službou. Oba klienti komunikují se službou pomocí konfigurace zadané v souboru Test. config.

 Následující kód přidá vlastní konfigurační soubor do klientské aplikace.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete Visual Studio 2012 s oprávněními správce.

2. Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projekty) a pak vyberte **vlastnosti**.

3. V nabídce **běžné vlastnosti**vyberte možnost **projekt po spuštění**a pak klikněte na **více projektů po spuštění**.

4. Přesuňte projekt **služby** na začátek seznamu a **akci ' Start '** a poté přesuňte **klientský** projekt za projekt **služby** , a to také pomocí **akce ' spustit '** , takže se **klientský** projekt spustí po projektu **služby** .

5. Klikněte na **OK**a potom stisknutím klávesy F5 (nebo CTRL + F5) spusťte ukázku.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
