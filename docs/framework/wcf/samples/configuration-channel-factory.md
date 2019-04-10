---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 5bee4c7cc2c2e64c6e0d8d0ec2634f9500cd9d51
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328072"
---
# <a name="configuration-channel-factory"></a>Postup konfiguračního kanálu
Tento příklad zahrnuje použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umožňuje centrální správu z konfigurace klienta WCF. To může být užitečné v situacích, ve kterých je konfigurace vybrané nebo změnit po dobu načítání domény aplikace.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Diskuse
 Tento příklad ukazuje způsob použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli používat výchozí konfigurační soubor aplikace.

 Vzorek se skládá ze dvou projektů. První projekt je jednoduchou službu, na kterém běží odpovídání na zprávy přicházející z klientů. Je druhý projekt klientské aplikace, který vytváří dvě <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objektů pomocí <xref:System.Configuration.ExeConfigurationFileMap> Test.config konfiguračního souboru a použije je ke komunikaci se službou. Oba klienti komunikaci se službou pomocí zadané v Test.config konfigurace.

 Následující kód přidá vlastní konfigurační soubor do klientské aplikace.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Otevřete Visual Studio 2012 s oprávněními správce.

2. Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projektů) a pak vyberte **vlastnosti**.

3. V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **více projektů po spuštění**.

4. Přesunout **služby** projekt na začátku seznamu, se **akce 'Start'** a poté přesuňte **klienta** projektu po **služby**projektu, také se **akce 'Start'**, takže **klienta** projektu se spustí až po **služby** projektu.

5. Klikněte na tlačítko **OK**a potom stiskněte klávesu F5 (nebo CTRL + F5) ke spuštění ukázky.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
