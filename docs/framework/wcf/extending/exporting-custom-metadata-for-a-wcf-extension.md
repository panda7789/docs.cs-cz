---
title: Export vlastních metadat pro rozšíření WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797192"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Export vlastních metadat pro rozšíření WCF
V Windows Communication Foundation (WCF) je export metadat proces popsání koncových bodů služby a jejich prochází paralelně standardizovanými reprezentacemi, které mohou klienti použít k pochopení toho, jak službu používat. Vlastní metadata se skládají z elementů XML, které nemohou exportovat vývozci metadat systému. Obvykle to zahrnuje vlastní prvky WSDL pro uživatelsky definované chování a prvky vazby a kontrolní výrazy zásad týkající se možností a požadavků vazeb a smluv.  
  
 Tato část popisuje Export vlastních kontrolních výrazů WSDL nebo zásad a nezaměřuje se na samotný proces exportu. Další informace o tom, jak používat typy, které exportují a importují metadata bez ohledu na to, jestli jsou metadata vlastní nebo založené na systému, najdete v tématu [Export a import metadat](../feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Přehled  
 Když jsou metadata publikována pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> , je zkontrolováno a XSD a WSDL--včetně kontrolních výrazů zásad – jsou generovány pro všechny kontrakty a vazby, které může WCF podporovat pomocí atributů a vazeb poskytovaných systémem. Nicméně atributy vlastního chování nebo prvky vazby vyžadují podporu, aby bylo možné správně exportovat.  
  
 Tato část popisuje:  
  
1. Jak implementovat a používat <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> rozhraní, které zpřístupňuje data generování WSDL před publikováním WSDL.  
  
2. Jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní, které zpřístupňuje data zásad před exportem kontrolních výrazů zásad v datech WSDL.  
  
 Další informace o importu vlastních kontrolních výrazů WSDL a zásad najdete v tématu [Import vlastních metadat pro rozšíření WCF](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Export vlastních elementů WSDL  
 <xref:System.ServiceModel.Description.IContractBehavior><xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior>Implementujte chování operace, chování kontraktu, chování koncového bodu nebo elementu vazby (,, nebo v uvedeném pořadí) a vložte chování nebo prvky vazby do <xref:System.ServiceModel.Description.IWsdlExportExtension> Popis služby, kterou se pokoušíte exportovat (Další informace o vkládání chování najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Je volána pro každý koncový bod a každý koncový bod nejprve exportuje kontrakt, pokud ještě nebyl exportován. V závislosti na vašich potřebách se můžete zúčastnit buď procesu exportu:  
  
- Použijte k úpravě exportovaných metadat <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> v metodě. <xref:System.ServiceModel.Description.WsdlContractConversionContext>  
  
- Použijte k úpravě exportovaných metadat pro koncový bod <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> v metodě. <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>  
  
 Metoda je volána pro všechny <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace v rámci <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> exportované instance. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>  Metoda je volána pro všechny <xref:System.ServiceModel.Description.IWsdlExportExtension> implementace s <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instancí, která je exportována. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>  
  
 Další informace najdete v tématu [jak: Exportujte vlastní WSDL](how-to-export-custom-wsdl.md) a ukázku [vlastní publikace WSDL](../samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
 Implementujte na a a přidejte do vazby element vazby, abyste mohli napsat vlastní kontrolní výrazy zásad týkající se podpory vazeb a možností kontraktu do WSDL. <xref:System.ServiceModel.Channels.BindingElement> <xref:System.ServiceModel.Description.IPolicyExportExtension> Je volána jednou při exportu implementovaného prvku vazby ve vazbě a <xref:System.ServiceModel.Description.PolicyConversionContext> předá do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody. <xref:System.ServiceModel.Description.IPolicyExportExtension> Můžete použít metody v <xref:System.ServiceModel.Description.PolicyConversionContext> instanci pro přidání k kontrolním výrazům zásad připojeným k vazbě WSDL v předmětech zprávy, operace nebo koncového bodu.  
  
 Další informace najdete v tématu [jak: Exportujte kontrolní výrazy](how-to-export-custom-policy-assertions.md)vlastních zásad.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Exportovat vlastní WSDL](how-to-export-custom-wsdl.md)
- [Postupy: Export kontrolních výrazů vlastních zásad](how-to-export-custom-policy-assertions.md)
- [Import vlastních metadat pro rozšíření WCF](importing-custom-metadata-for-a-wcf-extension.md)
