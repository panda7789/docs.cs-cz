---
title: Přístup k OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 8d1c8543180a282a1b196393e5823dc3686aa16e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038410"
---
# <a name="accessing-operationcontext"></a>Přístup k OperationContext
Tato ukázka předvádí, jak se aktivity<xref:System.ServiceModel.Activities.Receive> zasílání zpráv (a <xref:System.ServiceModel.Activities.Send>) dají použít s aktivitou vlastního <xref:System.ServiceModel.OperationContext.Current%2A> oboru pro přístup a připojení nebo načtení vlastní hlavičky zprávy v odchozí nebo příchozí zprávě.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivity zasílání <xref:System.ServiceModel.Activities.ISendMessageCallback>zpráv <xref:System.ServiceModel.Activities.IReceiveMessageCallback>,,.  
  
## <a name="discussion"></a>Účely  
 V této ukázce se dozvíte, jak používat<xref:System.ServiceModel.Activities.ISendMessageCallback>body <xref:System.ServiceModel.Activities.IReceiveMessageCallback>rozšiřitelnosti ()) v aktivitách zasílání zpráv pro přístup <xref:System.ServiceModel.OperationContext.Current%2A>. Zpětná volání jsou registrována v rámci modulu runtime pracovního postupu jako <xref:System.Activities.IExecutionProperty> implementace, kterou po spuštění vybraly aktivity zasílání zpráv. Ovlivněny budou všechny aktivity zasílání zpráv ve <xref:System.Activities.IExecutionProperty> stejném oboru jako tato implementace. Konkrétně tato ukázka používá vlastní aktivitu oboru k vykonání chování zpětného volání. Používá se v pracovním postupu klienta k zahrnutí <xref:System.Activities.WorkflowApplication.Id%2A> pracovního postupu jako odchozího <xref:System.ServiceModel.Channels.MessageHeader>. <xref:System.ServiceModel.Activities.ISendMessageCallback> Tato hlavička se pak ve službě vybrala pomocí <xref:System.ServiceModel.Activities.IReceiveMessageCallback> a hodnota hlavičky se vytiskne na konzolu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP. Pokud chcete tuto ukázku spustit, musí se přidat správné seznamy ACL adresy URL (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ), a to buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními, abyste přidali příslušné seznamy ACL. Ujistěte se, že je nahrazena vaše doména a uživatelské jméno.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání seznamů ACL adresy URL použijte následující postup.  
  
    1. Sestavte řešení.  
  
    2. Nastavte více spouštěcích projektů kliknutím pravým tlačítkem na řešení a výběrem možnosti **nastavit projekty po spuštění**.  
  
    3. Přidejte **službu** a **klienta** (v tomto pořadí) jako několik spouštěcích projektů.  
  
    4. Spusťte aplikaci. Konzola klienta zobrazuje dvakrát spuštěný pracovní postup a okno služby zobrazuje ID instance těchto pracovních postupů.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
