---
title: Korelace na základě obsahu
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: b90d076d96e1bae5c44dc1c2b06f826d256f7463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="content-based-correlation"></a>Korelace na základě obsahu
Tento příklad ukazuje, jak aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>) lze použít s více na základě obsahu correlations.and korelace na základě obsahu. V tomto scénáři korelace první inicializaci podle ID nákupní objednávky, a dále jiné korelace se později podle ID zákazníka. Ukazuje to, jak <xref:System.ServiceModel.Activities.Receive> aktivity můžete postupovat podle existujících korelace i inicializovat nové korelace na základě stejné příchozí zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivity zasílání zpráv a korelace na základě obsahu  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak používat více na základě obsahu korelací.  V tomto scénáři korelace první inicializaci podle ID nákupní objednávky, a dále jiné korelace se později podle ID zákazníka.  Korelací jsou kaskádové pomocí <xref:System.ServiceModel.Activities.Receive> aktivity, která odpovídá existující korelace (PurchaseOrderId) i inicializuje nový korelace (CustomerId) podle stejné příchozí zprávy.  K tomu <xref:System.ServiceModel.Activities.Receive> používá aktivitu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> a <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.  
  
2.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CascadingCorrelation.sln.  
  
3.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
4.  Pokud chcete spustit serveru, stisknutím klávesy F5.  
  
5.  Jakmile služba je připravena a naslouchání pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte ji.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`