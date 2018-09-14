---
title: Trvalá prodleva v XAMLX
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594093"
---
# <a name="durable-delay-in-xamlx"></a>Trvalá prodleva v XAMLX
Tato ukázka demonstruje použití trvalá prodleva, což je zpoždění, které se přenese pracovního postupu odolné zařízení během zpoždění.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Diskuse  
 Ukázkový pracovní postup obsahuje dvě zprávy do místního souboru, které jsou odděleny ke zpoždění. Když se aktivuje zpoždění, pracovní postup bude uvolněna a čeká 5 sekund do úložiště instancí pracovních postupů, než se znovu načten v paměti.  
  
 Soubor .xamlx je služby pracovního postupu, který je hostován v sadě Visual Studio. Visual Studio používá Cassini, který používá hostiteli služby pracovního procesu pracovního postupu.  
  
 Kromě hostování pracovního postupu, spravuje hostitele služby pracovního postupu instancí pracovních postupů pomocí načítání a uvolňování je. Spustit instanci Windows Workflow Foundation (WF) definice (na hostiteli služby pracovního postupu), nastavení klienta, která odesílá zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. To <xref:System.ServiceModel.Activities.Receive> má jeho <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> nastavenou na `true`, bude moct vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.  
  
 Během inicializace uvolnění instance chování přidáno do konfiguračního souboru, který určuje k hostiteli služby pracovního postupu, pod kterým ji by měl uvolnit instance do trvalého úložiště (databáze). V tomto příkladu je uvolněn instance okamžitě po ukončení pracovního postupu nečinnosti (v případě, že se aktivuje zpoždění).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do složky DurableDelayXamlx\CS.  
  
3.  Spusťte Setup.cmd.  
  
4.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.  
  
5.  Otevřete soubor řešení DurableDelayXamlx.sln.  
  
6.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.  
  
7.  Vyberte **více projektů po spuštění** a nastavte oba projekty **Start**.  
  
8.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
9. Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
#### <a name="to-uninstall-this-sample"></a>Chcete-li odinstalovat tuto ukázku  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do složky DurableDelayXamlx\CS.  
  
3.  Spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
