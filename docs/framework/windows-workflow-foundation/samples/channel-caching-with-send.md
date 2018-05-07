---
title: Ukládání do mezipaměti s odesílání kanálu
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: c26d81b9cd85ba75189fafddd82c3fb4673c7fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="channel-caching-with-send"></a>Ukládání do mezipaměti s odesílání kanálu
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Umožňuje uživatelům mají různé úrovně kanál ukládání do mezipaměti s <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendParametersContent> aktivity. Ve výchozím nastavení je povoleno ukládání do mezipaměti úrovni instance a tento příklad znázorňuje následující funkce:  
  
1.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> napříč domény aplikace.  
  
2.  Zakažte kanál ukládání do mezipaměti.  
  
3.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezi instancí pracovních postupů v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Spusťte aplikaci EchoWorkflowService vygenerovaných \EchoWorkflowService\bin\debug.  
  
3.  Spusťte aplikaci EchoWorkflowClient vygenerovaných .\EchoWorkflowClient\bin\debug.  
  
4.  Klient volá operaci odezvu na službu a zobrazí výsledky. Vytištěné výsledky stisknutím klávesy ENTER ukončete klienta a služby.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
