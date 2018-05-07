---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Viz také
