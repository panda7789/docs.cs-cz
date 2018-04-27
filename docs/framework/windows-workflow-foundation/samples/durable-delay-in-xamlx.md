---
title: Trvanlivý zpoždění při XAMLX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d7377d843e4ab8bd583e135dcdfd2cbfca67b8d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="durable-delay-in-xamlx"></a>Trvanlivý zpoždění při XAMLX
Tento příklad znázorňuje způsob použití trvanlivý zpoždění, což je zpoždění, která je uchována pracovního postupu trvanlivý zařízení během zpoždění.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Diskusní  
 Ukázkový pracovní postup obsahuje dvě zprávy do místního souboru, které jsou odděleny zpoždění. Když se aktivuje zpoždění pracovní postup je odpojen a čeká 5 sekund v úložišti instance pracovního postupu, než se znovu načíst v paměti.  
  
 Soubor .xamlx je služby pracovního postupu, který je hostován v sadě Visual Studio. Visual Studio použije Cassini, který používá hostiteli služby pracovního procesu pracovního postupu.  
  
 Kromě hostování pracovního postupu, spravuje hostitele služby pracovního postupu instancí pracovních postupů tím, načítání a uvolňování je. Spustit instanci [!INCLUDE[wf](../../../../includes/wf-md.md)] definice (na hostiteli služby pracovního postupu), nastavení klienta, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. To <xref:System.ServiceModel.Activities.Receive> má jeho <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> vlastnost nastavena na hodnotu `true`, kterých je možné vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.  
  
 Během inicializace uvolnění instance chování je do konfiguračního souboru, který určuje, že hostitel služby pracovního postupu, pod kterým je by uvolnit instance do úložiště trvalosti (databáze). Tato ukázka se uvolní instanci, ihned po pracovní postup přejde nečinnosti (když se spustí zpoždění).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do složky DurableDelayXamlx\CS.  
  
3.  Spusťte Setup.cmd.  
  
4.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.  
  
5.  Otevřete soubor řešení DurableDelayXamlx.sln.  
  
6.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.  
  
7.  Vyberte **více projektů po spuštění** a nastavte oba projekty **spustit**.  
  
8.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
9. Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
#### <a name="to-uninstall-this-sample"></a>Chcete-li odinstalovat tuto ukázku  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do složky DurableDelayXamlx\CS.  
  
3.  Spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
