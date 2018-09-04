---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525418"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Tento příklad ukazuje, jak vložit vlastní XML metadat do zjišťování metadat pro koncový bod zjistitelné vystavený službou. Ukázka pak ukazuje, jak extrahovat tento vlastní data a vyhledání služby klienta. Tato ukázka se skládá ze dvou projektů, klienta a služby.  
  
## <a name="service"></a>Služba  
 V `main` metody, příklad ukazuje, že objekt typu <xref:System.Xml.Linq.XElement> se vyplní požadované pole a je přidán <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se přidá do konkrétní koncový bod. Při zjištění tohoto konkrétního koncového bodu zjišťování metadat obsahuje vlastní data, která byla přidána tady.  
  
## <a name="client"></a>Klient  
 Vzorek ukazuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda se volá na <xref:System.ServiceModel.Discovery.DiscoveryClient>. Výsledná <xref:System.ServiceModel.Discovery.FindResponse> pak dotaz na prvky XML odpovídající a očekávané. Tyto prvky jsou pak vytištěna do konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načítání řešení projektu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.  
  
2.  Nejprve spusťte aplikaci služby, vygenerované v \service\bin\debug [základní adresář řešení] a pak spusťte klientská aplikace vygenerované v \Client\bin\debug [základní adresář řešení]  
  
3.  Všimněte si, že služba převede do režimu online, klient vyhledá službu a vypíše publikovat koncový bod metadat.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Viz také
