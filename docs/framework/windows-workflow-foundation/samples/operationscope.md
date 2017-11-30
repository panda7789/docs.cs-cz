---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b90ab7e38f40cb515166d4d08e0316ffb9061be3
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="operationscope"></a>OperationScope
Tento příklad ukazuje, jak aktivity, zasílání zpráv <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> můžete použít k vystavení existující vlastní aktivity jako operaci v služby pracovních postupů. Tato ukázka obsahuje novou vlastní aktivitu volána `OperationScope`. Je určena k usnadnění vývoje služby pracovního postupu tak, že umožníte uživatelům vytvářet text činnosti samostatně jako vlastní aktivity a pak je snadno vystavení jako operací služby pomocí `OperationScope` aktivity. Například vlastní `Add` aktivity, která přebírá dva `in` argumentů a vrátí jeden `out` může dojít k vystavení argument jako `Add` provozní stav služby pracovního postupu umístěním do `OperationScope`.  
  
 Obor funguje tak, že zkontrolujete aktivity zadaný jako její text. Žádné nevázaných `in` argumenty se předpokládá, že vstupy z příchozí zprávy. Všechny `out` argumenty, bez ohledu na to, jestli je vázána, se předpokládá, že výstupy v následných odpovědi. Název zveřejněné operace jsou převzaty z zobrazovaný název `OperationScope` aktivity. Konečným výsledkem je, že aktivita textu je uzavřen do <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> s parametry ze zprávy vázána na argumenty aktivity.  
  
 Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP. Pokud chcete spustit, je nutné přidat seznamy ACL správnou adresu URL. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Provádění řádku se zvýšenými oprávněními následující příkaz přidá příslušné seznamy ACL (zajistit, aby uživatelské jméno a doména jsou nahrazována pro domény %\\% UserName %).  
  
 **netsh http přidejte adresu url urlacl = http: / / +: 8000 / uživatele domény % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení OperationScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  V Průzkumníku řešení kliknete pravým tlačítkem a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**. Přidejte jako více projektů spuštění scénář a Scenario_Client (v tomto pořadí).  
  
3.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
    > [!WARNING]
    >  Tento krok je nutný k zobrazení z důvodu vlastní aktivity pracovního postupu BankService.xaml `OperationScope`.  
  
4.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci. Konzole Scenario_Client vás vyzve k zadání vstupy a odpovídající výstup je vidět v konzole pro scénář.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`