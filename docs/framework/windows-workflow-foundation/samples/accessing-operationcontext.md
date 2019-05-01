---
title: Přístup k OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: c104ceb22117d7cc53050a6513a4aea58fdff8c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005599"
---
# <a name="accessing-operationcontext"></a>Přístup k OperationContext
Tato ukázka předvádí, jak zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.Send>) je možné s aktivitou vlastní obor pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A> připojit a načíst vlastní hlavičky v rámci odchozí nebo příchozí zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zasílání zpráv aktivity, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje způsob použití bodů rozšiřitelnosti (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) v zasílání zpráv aktivity pro přístup k <xref:System.ServiceModel.OperationContext.Current%2A>. Tak potřebná zpětná volání jsou registrovány v rámci modulu runtime pracovního postupu jako implementace <xref:System.Activities.IExecutionProperty> , který převezme zasílání zpráv aktivity při spuštění. Všechny aktivity zasílání zpráv ve stejném oboru jako <xref:System.Activities.IExecutionProperty> vliv implementace. Konkrétně Tato ukázka používá vlastní obor aktivit k vynucení chování zpětného volání. <xref:System.ServiceModel.Activities.ISendMessageCallback> Se používá v pracovním postupu klienta pracovního postupu zahrnout <xref:System.Activities.WorkflowApplication.Id%2A> jako odchozí <xref:System.ServiceModel.Channels.MessageHeader>. Tato hlavička pak převezme služby pomocí <xref:System.ServiceModel.Activities.IReceiveMessageCallback> a hodnota hlavičky se vytiskne na konzolu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Tato ukázka poskytuje služby pracovního postupu pomocí koncových bodů HTTP. Chcete-li spustit ukázku, správné seznamy ACL adresa URL musí být přidán (naleznete v tématu [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), buď pomocí sady Visual Studio jako správce nebo spuštěním následujícího příkazu na řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Ujistěte se, že jsou nahrazeny doména a uživatelské jméno.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání se seznamy ACL adresu URL, pomocí následujícího postupu.  
  
    1. Sestavte řešení.  
  
    2. Nastavení více projektů spuštění tak, že kliknete pravým tlačítkem řešení a vyberete **nastavit projekty po spuštění**.  
  
    3. Přidat **služby** a **klienta** (v uvedeném pořadí) jako více spuštění projektů.  
  
    4. Spusťte aplikaci. Konzola klienta zobrazí pracovní postup spuštěn dvakrát a okno služby Service ID instance pracovních postupů.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
