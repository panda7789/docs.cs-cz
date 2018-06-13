---
title: Přístup k informacím OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: cefbc3b10114b427518e640809462eedb131d695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516630"
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
