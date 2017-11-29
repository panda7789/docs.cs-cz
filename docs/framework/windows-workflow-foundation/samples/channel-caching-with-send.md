---
title: "Ukládání do mezipaměti s odesílání kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f78b22d1481e260535e4aeb9764d8ee349a7a2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="channel-caching-with-send"></a>Ukládání do mezipaměti s odesílání kanálu
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Umožňuje uživatelům mají různé úrovně kanál ukládání do mezipaměti s <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendParametersContent> aktivity. Ve výchozím nastavení je povoleno ukládání do mezipaměti úrovni instance a tento příklad znázorňuje následující funkce:  
  
1.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> napříč domény aplikace.  
  
2.  Zakažte kanál ukládání do mezipaměti.  
  
3.  Sdílené složky <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezi instancí pracovních postupů v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>rozšíření, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
