---
title: Ukázka koncového bodu správy pracovního postupu
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 3d99cbef20895381f5e40ee939e1d94a409f1391
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485256"
---
# <a name="workflow-management-endpoint-sample"></a>Ukázka koncového bodu správy pracovního postupu
Tento příklad ukazuje použití ovládacího prvku koncový bod pracovního postupu vytvoření a spuštění pracovních postupů, místně i vzdáleně. Vzorek ukazuje, jak hostovat koncové body typu ovládacího prvku a zápis klientů, které volají kontrolní koncový bod pro vytvoření a spuštění instance pracovního postupu. Pracovní postup není služba.  
  
 Na straně služby vzorku je hostovaný pracovního postupu pomocí třídy WorkflowServiceHost a přidá koncového bodu WorkflowControlEndpoint tak, aby klienti můžou provádět operace správy (pozastavit, Start atd.). Uživatelem definované CreationEndpoint je taky přidaný ke povolit pracovní postup, který se má vytvořit. Služba potom použije tyto koncové body pro spuštění pracovního postupu v pozastaveném stavu a poté obnovit pracovního postupu. Klient provede stejné operace, ale z kódu klienta. Pro další informace o těchto rozhraní, naleznete v tématu [kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) a [postupy: hostování pracovního postupu bez služby ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.  
  
2.  Otevřete řešení ManagementEndpoint.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
4.  Spusťte aplikaci ManagementEndpoint.exe.  
  
5.  Spusťte aplikaci Client.exe.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`