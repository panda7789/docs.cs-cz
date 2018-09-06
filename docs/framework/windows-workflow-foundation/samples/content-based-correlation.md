---
title: Korelace na základě obsahu
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: c0367f480701468dcd5024ea3439bdcd38acc78f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731719"
---
# <a name="content-based-correlation"></a>Korelace na základě obsahu
Tato ukázka předvádí, jak zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>) lze použít s více založené na obsahu correlations.and založené na obsahu korelace. V tomto scénáři korelaci první inicializaci podle ID nákupní objednávky a pak další korelace je vytvořen později podle ID zákazníka. To ukazuje, jak <xref:System.ServiceModel.Activities.Receive> aktivity můžete postupovat podle existujících korelace i inicializuje novou korelaci. na základě stejné příchozí zprávy.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivity zasílání zpráv a korelace na základě obsahu  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje způsob použití více korelace založené na obsahu.  V tomto scénáři korelaci první inicializaci podle ID nákupní objednávky a pak další korelace je vytvořen později podle ID zákazníka.  Korelace jsou kaskádové pomocí <xref:System.ServiceModel.Activities.Receive> aktivitu, která následuje existující korelace (PurchaseOrderId) i inicializuje novou korelaci. (ID zákazníka) na základě stejné příchozí zprávy.  K tomu, <xref:System.ServiceModel.Activities.Receive> používá aktivitu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> a <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnosti.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.  
  
2.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CascadingCorrelation.sln.  
  
3.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
4.  Spusťte server, stiskněte klávesu F5.  
  
5.  Jakmile služba je připravená a naslouchá pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte jej.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`