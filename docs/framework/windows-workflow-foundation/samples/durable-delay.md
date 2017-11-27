---
title: "Trvanlivý zpoždění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7023d7548db99d511ae18ad4d52b9a8168c4243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="durable-delay"></a>Trvanlivý zpoždění
Tento příklad znázorňuje způsob použití trvanlivý zpoždění, což je zpoždění, která je uchována pracovního postupu trvanlivý zařízení během zpoždění. Ukázkový pracovní postup obsahuje dvě zpráv do konzoly, které jsou odděleny zpoždění. Když se aktivuje zpoždění pracovní postup je odpojen a čeká 5 sekund v úložišti instance pracovního postupu, než se znovu načíst v paměti.  
  
## <a name="workflow-details"></a>Podrobnosti pracovního postupu  
 Hostitel služby pracovního postupu hostuje pracovního postupu a instance pracovního postupu podle načítání a uvolňování je spravuje. Pokud chcete spustit instance definice pracovního postupu, ukázky nastaví proxy server, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Je nastavena na `true`, kterých je možné vytvořit novou instanci pracovního postupu, jakmile obdrží zprávu.  
  
 Následující seznam popisuje, o nastavení hostitele služby pracovního postupu během inicializace.  
  
1.  Vytvoří hostitele služby s adresou (adrese http://localhost: 8080/klienta).  
  
2.  Vytvoří koncový bod na hostiteli služby k umožnění komunikace s <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.  
  
3.  Nastaví instance úložiště SQL.  
  
4.  Přidá uvolnění instance chování, které určuje podmínky, za kterých by měl hostitel služby pracovního postupu uvolnit instanci pracovního postupu do úložiště trvalosti SQL. Tato ukázka se uvolní instanci, ihned po pracovní postup přejde nečinnosti (když se spustí zpoždění).  
  
5.  Vytvoří proxy server, který odešle zprávu, která <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Nastavení databáze trvalost.  
  
    1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adresáře (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Upravte soubor WorkflowManagementService.exe.config a přidejte následující připojovací řetězec uvnitř <`database`> elementu.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Přejděte do adresáře DurableDelay\CS.  
  
    5.  Spusťte Setup.cmd.  
  
2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pomocí zvýšenými oprávněními kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.  
  
3.  Otevřete soubor řešení Delay.sln.  
  
4.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
5.  Stisknutím kombinace kláves CTRL + F5 a spusťte řešení.  
  
#### <a name="to-uninstall-this-sample"></a>Chcete-li odinstalovat tuto ukázku  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do adresáře DurableDelay\CS.  
  
3.  Spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`  
  
## <a name="see-also"></a>Viz také
