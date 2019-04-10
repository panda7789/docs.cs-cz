---
title: 'Postupy: Export kontrolních výrazů vlastních zásad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 4e3835b0d699d58eb55e06ed3ade1328ec30b2ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213606"
---
# <a name="how-to-export-custom-policy-assertions"></a>Postupy: Export kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad popisují funkce a požadavky koncového bodu služby. Aplikace služby můžete použít kontrolních výrazů vlastních zásad v metadata služby pro komunikaci koncový bod, informace o přizpůsobení vazby nebo smlouvy do klientské aplikace. Export kontrolních výrazů ve výrazech zásad připojena v vazby WSDL na koncový bod, operace nebo zprávy témata, v závislosti na možnosti nebo požadavky, které komunikují se můžete použít Windows Communication Foundation (WCF).  
  
 Kontrolních výrazů vlastních zásad jsou exportovány implementací <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> na rozhraní <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a buď vložení elementu vazby přímo do vazby koncového bodu služby nebo si zaregistrujte ve vaší aplikaci prvku vazby konfigurační soubor. Implementace export zásad by měl přidat vaše vlastní zásady pro kontrolní výraz jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance na příslušné <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> předán <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> – metoda.  
  
 Kromě toho je nutné zkontrolovat <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter> třídy a export zásad vnořených výrazů a atributů framework zásad v správný obor názvů na základě zadané verze zásad.  
  
 Import kontrolních výrazů vlastních zásad, najdete v článku <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a [jak: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
  
1.  Implementace <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> na rozhraní <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Následující příklad kódu ukazuje implementaci kontrolní výraz vlastní zásady na úrovni vazby.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Vložte element vazby do koncového bodu vazba buď programově, nebo pomocí konfiguračního souboru aplikace. Podívejte se na následující postupy.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Chcete-li vložit prvek vazby, který je používán konfigurační soubor aplikace  
  
1.  Implementace <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> pro element vazby vaše vlastní zásady pro kontrolní výraz.  
  
2.  Přidat do souboru pomocí konfigurace rozšíření elementu vazby [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elementu.  
  
3.  Vytvoření vlastní vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Chcete-li vložit element vazby prostřednictvím kódu programu  
  
1.  Vytvořte nový <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a přidejte ji tak <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Přidáte vlastní vazbu z kroku 1. Nový koncový bod a přidejte tento nový koncový bod služby <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.  
  
3.  Otevřít <xref:System.ServiceModel.ServiceHost>. Následující příklad kódu ukazuje vytvoření vlastní vazby a programové vkládání elementů vazby.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
