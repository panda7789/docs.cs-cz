---
title: Přístup k OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 5a2731c7918c216221b0adcafd5c804e80f36dfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182861"
---
# <a name="accessing-operationcontext"></a>Přístup k OperationContext
Tato ukázka ukazuje, jak<xref:System.ServiceModel.Activities.Receive> mohou <xref:System.ServiceModel.Activities.Send>být aktivity zasílání zpráv ( <xref:System.ServiceModel.OperationContext.Current%2A> a ) použity s vlastní aktivitou oboru pro přístup a připojení nebo načtení záhlaví vlastní zprávy v rámci odchozí nebo příchozí zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivity zasílání <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback>zpráv , .  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka ukazuje, jak používat<xref:System.ServiceModel.Activities.ISendMessageCallback>body <xref:System.ServiceModel.Activities.IReceiveMessageCallback>rozšiřitelnosti ( <xref:System.ServiceModel.OperationContext.Current%2A>) ) v aktivitách zasílání zpráv pro přístup . Zpětná volání jsou registrovány v rámci běhu <xref:System.Activities.IExecutionProperty> pracovního postupu jako implementace, která je vyzvednuta aktivitami zasílání zpráv při spuštění. Všechny aktivity zasílání zpráv ve <xref:System.Activities.IExecutionProperty> stejném oboru jako tato implementace je ovlivněna. Zejména tato ukázka používá vlastní obor aktivity k vynucení chování zpětného volání. V <xref:System.ServiceModel.Activities.ISendMessageCallback> pracovním postupu klienta se používá <xref:System.Activities.WorkflowApplication.Id%2A> k zahrnutí <xref:System.ServiceModel.Channels.MessageHeader>pracovního postupu jako odchozího . Toto záhlaví je pak zvedl <xref:System.ServiceModel.Activities.IReceiveMessageCallback> ve službě pomocí a hodnota záhlaví je vytištěna do konzoly.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP. Chcete-li spustit tuto ukázku, musí být přidány správné adresy ACL správné adresy URL (viz [Konfigurace protokolu HTTP a HTTPS](../../wcf/feature-details/configuring-http-and-https.md) podrobnosti), buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu ve zvýšené výzvě k přidání příslušných seznamu ACL. Ujistěte se, že vaše doména a uživatelské jméno jsou nahrazeny.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání adres URL aklů použijte následující kroky.  
  
    1. Sestavte řešení.  
  
    2. Nastavte více počátečních projektů klepnutím pravým tlačítkem myši na řešení a výběrem **možnosti Nastavit projekty po spuštění**.  
  
    3. Přidejte **službu** a **klienta** (v tomto pořadí) jako více start-up projektů.  
  
    4. Spusťte aplikaci. Konzole klienta zobrazuje pracovní postup spuštěný dvakrát a okno Služba zobrazuje ID instance těchto pracovních postupů.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
