---
title: "Přístup k informacím OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a>Přístup k informacím OperationContext
Tento příklad ukazuje, jak aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.Send>) lze použít s aktivitou vlastní rozsah pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A> a připojit nebo načíst záhlaví vlastní zprávy v rámci odchozí nebo příchozí zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivity, zasílání zpráv <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje způsob použití body rozšiřitelnosti (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) v zasílání zpráv aktivity pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A>. V modulu runtime pracovního postupu jako implementaci jsou zaregistrována zpětná volání <xref:System.Activities.IExecutionProperty> , je převzata aktivitami zasílání zpráv při spuštění. Všechny aktivity zasílání zpráv ve stejném oboru, který <xref:System.Activities.IExecutionProperty> implementace má vliv. Konkrétně Tato ukázka používá aktivitu vlastní rozsah vynutit chování zpětného volání. <xref:System.ServiceModel.Activities.ISendMessageCallback> Se používá v pracovním postupu klienta zahrnout pracovního postupu <xref:System.Activities.WorkflowApplication.Id%2A> jako odchozí <xref:System.ServiceModel.Channels.MessageHeader>. Tuto hlavičku je pak zachyceny v služby pomocí <xref:System.ServiceModel.Activities.IReceiveMessageCallback> a hodnota hlavičky se vytiskne ke konzole.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP. Použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán (viz [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), spuštění sady Visual Studio jako správce, nebo spuštěním následujícího příkazu řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Zajistěte, aby uživatelské jméno a doména jsou nahrazována.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Jakmile se přidají adresy URL seznamy ACL, použijte následující postup.  
  
    1.  Sestavte řešení.  
  
    2.  Pravým tlačítkem myši řešení a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**.  
  
    3.  Přidat **služby** a **klienta** (v tomto pořadí) jako více projektů spuštění.  
  
    4.  Spusťte aplikaci. Konzole klienta ukazuje pracovní postup spuštěn dvakrát a zobrazí se okno Service ID instance pracovních postupů.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
