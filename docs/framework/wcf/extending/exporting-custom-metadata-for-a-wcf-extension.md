---
title: Export vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 5134b57c59268b139239021bc2b4f6f4538ad27d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334507"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Export vlastních metadat pro rozšíření WCF
Ve Windows Communication Foundation (WCF), export metadat je proces popisující koncové body služby a projekci na paralelní standardizované reprezentaci, který můžou klienti použít k vysvětlení použití služby. Vlastní metadata se skládá z elementů XML, které nelze exportovat vývozci poskytované systémem metadat. Obvykle obsahuje vlastní prvky WSDL pro uživatelem definované chování a prvky vazeb a výrazů zásad o funkce a požadavky vazby a kontrakty.  
  
 Tato část popisuje Export vlastního WSDL nebo kontrolní výrazy zásad a nezaměřuje na samotný proces exportu. Další informace o tom, jak používat typy, které export a import metadat bez ohledu na to, jestli metadata vlastní nebo vytvořen systému, naleznete v tématu [pro export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 Při publikování metadat pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> je zkontrolován a XSD a WSDL – včetně kontrolní výrazy zásad - jsou generovány pro všechny vazby, které podporuje WCF pomocí poskytnuté systémem atributy a vazby a kontrakty. Nicméně vlastní chování atributů nebo elementů vazby vyžadují podporu předtím, než je možné exportovat správně.  
  
 Tato část popisuje:  
  
1. Jak implementovat a používat <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní, které zveřejňuje data generování WSDL, před publikováním schématu WSDL.  
  
2. Jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní, které zpřístupňuje data zásad vám před exportem kontrolní výrazy zásad v datech WSDL.  
  
 Další informace o importu vlastního WSDL a kontrolní výrazy zásad najdete v tématu [import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Export vlastního WSDL prvků  
 Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension> na chování operace, kontrakt chování, chování koncového bodu nebo element vazby (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, nebo <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> v uvedeném pořadí) a vložte chování nebo elementů vazby do Popis služby, která chcete exportovat. (Další informace o vkládání chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Je volána pro každý koncový bod a každý koncový bod exportuje kontrakt nejprve pokud ho ještě již byla exportována. Můžete se zúčastnit buď procesu exportu v závislosti na vašich potřeb:  
  
-   Použití <xref:System.ServiceModel.Description.WsdlContractConversionContext> upravit exportované metadat v <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
-   Použití <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> upravit exportované metadata pro koncový bod <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Metoda je volána ve všech <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace v rámci <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> instanci, která je exportována.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Metoda je volána ve všech <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace s <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instanci, která je exportována.  
  
 Další informace najdete v tématu [jak: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) a ukázku [vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
 Implementace <xref:System.ServiceModel.Description.IPolicyExportExtension> na <xref:System.ServiceModel.Channels.BindingElement> a přidejte element vazby pro vazbu k zápisu kontrolních výrazů vlastních zásad o vazbách možnosti podpory a smlouvy do jazyka WSDL. <xref:System.ServiceModel.Description.IPolicyExportExtension> Je volána při exportu element implementované vazby ve vazbě a předává <xref:System.ServiceModel.Description.PolicyConversionContext> k <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody. Můžete použít metody na <xref:System.ServiceModel.Description.PolicyConversionContext> instance přidat kontrolní výrazy zásad připojen k Vazba WSDL na témata zpráv, operace nebo koncový bod.  
  
 Další informace najdete v tématu [jak: Export kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Postupy: Export kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
