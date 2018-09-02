---
title: Trvalá prodleva
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406573"
---
# <a name="durable-delay"></a>Trvalá prodleva
Tato ukázka demonstruje použití trvalá prodleva, což je zpoždění, které se přenese pracovního postupu odolné zařízení během zpoždění. Ukázkový pracovní postup obsahuje dvě zprávy do konzoly nástroje, které jsou odděleny ke zpoždění. Když se aktivuje zpoždění, pracovní postup bude uvolněna a čeká 5 sekund do úložiště instancí pracovních postupů, než se znovu načten v paměti.  
  
## <a name="workflow-details"></a>Podrobnosti pracovního postupu  
 Hostitel služby pracovního postupu pracovní postup hostuje a spravuje instancí pracovních postupů pomocí načítání a uvolňování je. Spuštění instance definice pracovního postupu, vzorku nastaví proxy server, která odesílá zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Je nastavena na `true`, aby mohla vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.  
  
 Následující seznam obsahuje podrobnosti o nastavení hostitele služby pracovního postupu při inicializaci.  
  
1.  Vytvoří hostitele služby s adresou (http://localhost:8080/Client).  
  
2.  Vytvoří koncový bod v hostiteli služby k umožnění komunikace s <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.  
  
3.  Nastaví úložiště instancí SQL.  
  
4.  Přidá chování instance uvolnění z paměti, který určuje podmínky, za kterých by měl hostitel služby pracovního postupu uvolnit instance pracovního postupu do úložiště trvalosti SQL. V tomto příkladu je uvolněn instance okamžitě po ukončení pracovního postupu nečinnosti (v případě, že se aktivuje zpoždění).  
  
5.  Vytvoří proxy, která odešle zprávu <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Nastavení databáze trvalosti.  
  
    1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Upravte soubor WorkflowManagementService.exe.config a přidejte následující připojovací řetězec uvnitř <`database`> element.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Přejděte do adresáře DurableDelay\CS.  
  
    5.  Spusťte Setup.cmd.  
  
2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pomocí zvýšenou úroveň oprávnění kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.  
  
3.  Otevřete soubor řešení Delay.sln.  
  
4.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
5.  Stisknutím kláves CTRL + F5 spusťte řešení.  
  
#### <a name="to-uninstall-this-sample"></a>Chcete-li odinstalovat tuto ukázku  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do adresáře DurableDelay\CS.  
  
3.  Spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`