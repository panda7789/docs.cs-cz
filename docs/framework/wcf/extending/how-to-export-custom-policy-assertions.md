---
title: "Postupy: Export kontrolních výrazů vlastních zásad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8620dec4997947df2dc7078e337a5e421d66c55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-custom-policy-assertions"></a>Postupy: Export kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad jsou popsány možnosti a požadavky koncového bodu služby. Aplikace služby můžete pomocí kontrolních výrazů vlastních zásad metadata služby komunikovat koncový bod, vazba nebo kontrakt informace o přizpůsobení do klientské aplikace. Můžete použít [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] export kontrolní výrazy ve výrazech zásad připojena v WSDL vazby na koncový bod, operace nebo zpráva tématům, v závislosti na možnosti nebo požadavky jsou komunikaci.  
  
 Exportují se implementací kontrolních výrazů vlastních zásad <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a buď vložení prvku vazby přímo do vazby koncového bodu služby nebo tím, že zaregistrujete prvku vazby v aplikaci konfigurační soubor. Export implementaci zásad měli přidat vaše vlastní zásady assertion jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance na příslušné <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> předaný do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metoda.  
  
 Kromě toho je nutné zkontrolovat <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter> třídy a export výrazy vnořené zásad a zásad framework atributy ve správný obor názvů na základě zásad verze zadané.  
  
 Chcete-li import kontrolních výrazů vlastních zásad, přečtěte si téma <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a [postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
  
1.  Implementace <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Následující příklad kódu ukazuje implementaci assertion vlastní zásady na úrovni vazby.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Vložení prvku vazby do koncového bodu vazba buď programově, nebo pomocí konfiguračního souboru aplikace. Postupujte podle následujících pokynů.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Chcete-li vložit element vazby pomocí konfiguračního souboru aplikace  
  
1.  Implementace <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> pro vaše vlastní zásady assertion vazby element.  
  
2.  Přidejte rozšíření element vazby do souboru konfigurace pomocí [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.  
  
3.  Vytvoření vlastní vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Vložení prvku vazby prostřednictvím kódu programu  
  
1.  Vytvořte novou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a přidejte ho do <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Přidáte vlastní vazby z kroku 1. na nový koncový bod a přidejte tento nový koncový bod služby k <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.  
  
3.  Otevřete <xref:System.ServiceModel.ServiceHost>. Následující příklad kódu ukazuje vytvoření vlastní vazby a programové vkládání elementů vazby.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [Postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
