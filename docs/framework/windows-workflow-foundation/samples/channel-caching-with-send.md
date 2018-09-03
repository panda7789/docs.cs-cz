---
title: Kanál do mezipaměti pomocí Send
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475852"
---
# <a name="channel-caching-with-send"></a>Kanál do mezipaměti pomocí Send
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Umožňuje uživatelům mají různé úrovně kanál ukládání do mezipaměti s <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendParametersContent> aktivity. Ve výchozím nastavení je povoleno ukládání do mezipaměti na úrovni instance a tato ukázka demonstruje následující funkce:  
  
1.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> napříč doménou aplikace.  
  
2.  Zakáže ukládání do mezipaměti kanálu.  
  
3.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezi instance pracovního postupu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Spusťte aplikaci EchoWorkflowService vygenerované v \EchoWorkflowService\bin\debug.  
  
3.  Spusťte aplikaci EchoWorkflowClient vygenerované v .\EchoWorkflowClient\bin\debug.  
  
4.  Klient volá operace odezvu na službu a vypíše výsledky. Výsledky dokončení tisku, stisknutím klávesy ENTER ukončete klienta a služby.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
