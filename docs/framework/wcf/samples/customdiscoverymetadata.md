---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b4a68204d8ae5d2a338d60498522810a557e575
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Tento příklad ukazuje způsob vložení vlastních metadat XML do zjišťování metadat pro koncový bod zjistitelný zveřejněný prostřednictvím služby. Ukázka pak ukazuje, jak klient vyhledejte službu a extrahovat tento vlastní data. Tato ukázka se skládá z dva projekty, klienta a služby.  
  
## <a name="service"></a>Služba  
 V `main` metody ukázky ukazuje, že objekt typu <xref:System.Xml.Linq.XElement> naplněný požadovaná pole a přidají se do <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> je přidán do konkrétní koncový bod. Pokud je zjištěno, že konkrétní koncový bod, zjišťování metadat obsahuje vlastní data, která byla přidána zde.  
  
## <a name="client"></a>Klient  
 Ukázka ukazuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda volaného na <xref:System.ServiceModel.Discovery.DiscoveryClient>. Výsledná <xref:System.ServiceModel.Discovery.FindResponse> je pak dotazován na elementy XML odpovídající a očekávané. Tyto prvky jsou pak vytištěny ke konzole.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načtení projektu řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.  
  
2.  Nejprve spusťte aplikaci služby, vygenerovaných \service\bin\debug [základní adresář řešení] a pak spusťte klientské aplikace, vygenerovaných \Client\bin\debug [základní adresář řešení]  
  
3.  Všimněte si, že služba přepne do režimu online, klient vyhledá službu a vypíše metadata publikované v koncovém bodě.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Viz také
