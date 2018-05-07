---
title: Export vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 8d9f5e223bb47fc8997f6509ec882b282e1ee8b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Export vlastních metadat pro rozšíření WCF
Ve Windows Communication Foundation (WCF), export metadat je proces popisující koncové body služby a projekce je do znázornění paralelní, standardizované, který můžou klienti používat pochopit, jak používat službu. Vlastní metadata se skládá z elementů XML, které vývozci poskytované systémem metadata nelze exportovat. Obvykle obsahuje vlastní elementy WSDL pro uživatelem definované chování a prvky vazeb a výrazy zásad o možnostech a požadavky vazby a kontrakty.  
  
 Tato část popisuje, export vlastního WSDL nebo výrazy zásad a není soustředit na samotný proces exportu. Další informace o tom, jak používat typy, které exportovat a importovat metadata bez ohledu na to, jestli je metadata vlastní nebo sestavený systému najdete v tématu [export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 Při publikování metadat pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> je zkontrolován a XSD a WSDL – včetně výrazy zásad – jsou generovány pro všechny vazby a kontrakty, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] může podporovat pomocí poskytované systémem atributy a vazeb. Ale chování vlastní atributy nebo prvky vazeb vyžadovat podporu předtím, než je možné exportovat správně.  
  
 Tato část popisuje:  
  
1.  Tom, jak implementovat a použít <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní, která zpřístupňuje data generování WSDL vám před publikováním schématu WSDL.  
  
2.  Tom, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní, která zpřístupňuje data zásad vám před exportem výrazy zásad v datech WSDL.  
  
 Další informace o importu vlastního WSDL a kontrolních výrazů zásad najdete v tématu [import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Export vlastního WSDL prvků  
 Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension> na operaci chování, kontrakt chování, chování koncového bodu nebo prvku vazby (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, nebo <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> v uvedeném pořadí) a vložte chování nebo prvky vazeb do Popis služby, která chcete exportovat. (Další informace o vkládání chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Je volána pro každý koncový bod a každý koncový bod exportuje kontrakt nejprve Pokud nebyla již exportovali. Můžete se účastnit buď procesu exportu, v závislosti na vašich potřeb:  
  
-   Použití <xref:System.ServiceModel.Description.WsdlContractConversionContext> k úpravě exportovaný metadat v <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metoda.  
  
-   Použití <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> k úpravě exportovaný metadata pro koncový bod v <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Metoda je volána na všech <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace v rámci <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> instanci, která je exportována.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Metoda je volána na všech <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace s <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instanci, která je exportována.  
  
 Další informace najdete v tématu [postupy: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) a ukázky [vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
 Implementace <xref:System.ServiceModel.Description.IPolicyExportExtension> na <xref:System.ServiceModel.Channels.BindingElement> a přidejte element vazby pro vazbu k zápisu kontrolních výrazů vlastních zásad o vazby možnosti podpory a kontrakt do schématu WSDL. <xref:System.ServiceModel.Description.IPolicyExportExtension> Je jednou volána při exportu prvku implementovaná vazby ve vazbě a předá <xref:System.ServiceModel.Description.PolicyConversionContext> k <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metoda. Můžete použít metody na <xref:System.ServiceModel.Description.PolicyConversionContext> instance pro přidání do výrazy zásad připojen k WSDL vazbu na témata zpráva, operace nebo koncový bod.  
  
 Další informace najdete v tématu [postupy: Export kontrolních výrazů zásad vlastní](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Postupy: Export kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)  
 [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
