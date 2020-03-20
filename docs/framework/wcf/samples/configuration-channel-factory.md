---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183952"
---
# <a name="configuration-channel-factory"></a>Postup konfiguračního kanálu
Tento vzorek zahrnuje použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. Umožňuje <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> centrální správu konfigurace klienta WCF. To může být také užitečné ve scénářích, ve kterých je konfigurace vybrána nebo změněna po čase načítání domény aplikace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Diskuse
 Tato ukázka ukazuje, jak přidat <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> konkrétní konfigurační soubor do klientské aplikace, aniž byste museli používat výchozí konfigurační soubor aplikace.

 Vzorek se skládá ze dvou projektů. První projekt je jednoduchá služba, která běží odpovědět na zprávy přicházející od klientů. Druhý projekt je klientská aplikace, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> která <xref:System.Configuration.ExeConfigurationFileMap> vytvoří dva objekty pomocí konfiguračního souboru Test.config a používá je ke komunikaci se službou. Oba klienti komunikují se službou pomocí konfigurace zadané v souboru Test.config.

 Následující kód přidá do klientské aplikace vlastní konfigurační soubor.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete Visual Studio 2012 s oprávněními správce.

2. Klepněte pravým tlačítkem myši na řešení ConfigurationChannelFactory (2 projekty) a potom vyberte **příkaz Vlastnosti**.

3. V **pole Společné vlastnosti**vyberte **možnost Projekt po spuštění**a klepněte na tlačítko Více projektů **po spuštění**.

4. Přesuňte projekt **služby** na začátek seznamu s **akcí "Start"** a potom přesuňte projekt **klienta** po projektu **služby,** také s **akcí "Start"**, takže projekt **klienta** je proveden po projektu **služby.**

5. Klepněte na **tlačítko OK**a potom spusťte ukázku stisknutím klávesy F5 (nebo CTRL+F5).

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
