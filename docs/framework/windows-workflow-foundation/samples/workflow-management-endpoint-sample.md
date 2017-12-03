---
title: "Ukázka koncový bod správy pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193620902d5bcc2b71f91a26518ab4b6560e6753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-management-endpoint-sample"></a>Ukázka koncový bod správy pracovního postupu
Tento příklad ukazuje, jak koncový bod pracovního postupu ovládací prvek slouží k vytváření a spouštění pracovních postupů místně i vzdáleně. Ukázka ukazuje, jak hostovat kontrolní koncový bod a zápis klientů volání kontrolní koncový bod vytvořit a spustit instance pracovního postupu. Pracovní postup není služba.  
  
 Na straně služby ukázku pracovního postupu je hostovaná s hostitele služby pracovního postupu a WorkflowControlEndpoint se přidá, aby klienti mohli provést operace ovládacího prvku (pozastavit, počáteční atd.). Uživatelem definované CreationEndpoint je taky přidaný ke povolit pracovní postup, který se má vytvořit. Služba pak použije tyto koncové body spustit pracovní postup v pozastaveném stavu a poté obnovit pracovního postupu. Klient provádí stejné operace, ale z kódu klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tato rozhraní najdete [kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) a [postupy: hostování bez služby pracovního postupu ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.  
  
2.  Otevřete řešení ManagementEndpoint.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
4.  Spusťte aplikaci ManagementEndpoint.exe.  
  
5.  Spusťte aplikaci Client.exe.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`