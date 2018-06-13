---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: fc3a564128e520133c2404a82438e692b1381875
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806575"
---
# <a name="configuration-channel-factory"></a>Postup konfiguračního kanálu
Tato ukázka obsahuje využití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umožňuje centrální správu konfigurace klienta WCF. To může být užitečný ve scénářích, ve kterých je konfigurace vybrali nebo změnit po doba načítání domény aplikace.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje způsob použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli použít výchozí konfigurační soubor aplikace.  
  
 Ukázkový soubor obsahuje dva projekty. První projekt je jednoduchý služba, která běží na odpovědi na zprávy přicházející z klientů. Druhý projekt je klientská aplikace, která vytvoří dvě <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objekty pomocí <xref:System.Configuration.ExeConfigurationFileMap> Test.config konfiguračního souboru a použije je k komunikovat se službou. Oba klienti komunikovat se službou pomocí konfigurace zadaná v Test.config.  
  
 Následující kód přidá vlastní konfigurační soubor do klientské aplikace.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] s oprávněními správce.  
  
2.  Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projektů) a potom vyberte **vlastnosti**.  
  
3.  V **společných vlastností**, vyberte **spouštěný projekt**a potom klikněte na **více projektů po spuštění**.  
  
4.  Přesunout **služby** projektu na začátek seznamu, s **akce 'Start'** a poté přesuňte **klienta** projektu po **služby**projektu, také s **akce 'Start'**, proto **klienta** projektu se spustí až po **služby** projektu.  
  
5.  Klikněte na tlačítko **OK**a potom stiskněte klávesu F5 (nebo CTRL + F5) ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
