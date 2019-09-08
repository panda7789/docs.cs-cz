---
title: 'Postupy: Export kontrolních výrazů vlastních zásad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795664"
---
# <a name="how-to-export-custom-policy-assertions"></a>Postupy: Export kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad popisují možnosti a požadavky koncového bodu služby. Aplikace služby můžou použít vlastní kontrolní výrazy zásad v metadatech služby ke komunikaci koncových bodů, vazeb nebo informací o přizpůsobení smlouvy pro klientskou aplikaci. Pomocí Windows Communication Foundation (WCF) můžete exportovat kontrolní výrazy ve výrazech zásad připojených v rámci vazeb WSDL v závislosti na tom, jaké možnosti nebo požadavky komunikujete.  
  
 Vlastní kontrolní výrazy zásad jsou exportovány implementací <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> v a a buď vložení elementu vazby přímo do vazby koncového bodu služby, nebo registrací elementu vazby v aplikaci. konfigurační soubor. Implementace exportu zásad by měla přidat kontrolní <xref:System.Xml.XmlElement?displayProperty=nameWithType> výraz vlastní zásady jako instanci do příslušné <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metody v <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> předané metodě.  
  
 Kromě toho musíte zaškrtnout <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter> třídy a exportovat vnořené výrazy zásad a atributy architektury zásad do správného oboru názvů na základě zadané verze zásad.  
  
 Chcete-li importovat vlastní kontrolní výrazy zásad <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> , [Přečtěte si téma a postupy: Importujte vlastní kontrolní výrazy](how-to-import-custom-policy-assertions.md)zásad.  
  
### <a name="to-export-custom-policy-assertions"></a>Export kontrolních výrazů vlastních zásad  
  
1. Implementujte <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>rozhraní na. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> Následující příklad kódu ukazuje implementaci kontrolního výrazu vlastní zásady na úrovni vazby.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Vložte prvek vazby do vazby koncového bodu buď prostřednictvím kódu programu, nebo pomocí konfiguračního souboru aplikace. Projděte si následující postupy.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Vložení elementu vazby pomocí konfiguračního souboru aplikace  
  
1. Implementujte <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> pro vlastní element vazby kontrolního výrazu.  
  
2. Přidejte rozšíření elementu vazby do konfiguračního souboru pomocí [ \<elementu bindingElementExtensions >](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .  
  
3. Vytvořte vlastní vazbu pomocí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Postup pro vložení elementu vazby prostřednictvím kódu programu  
  
1. Vytvořte nový <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a přidejte ho <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>do.  
  
2. Přidejte vlastní vazbu z kroku 1. do nového koncového bodu a přidat tento nový koncový bod služby <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> k rozhraní <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> voláním metody.  
  
3. <xref:System.ServiceModel.ServiceHost>Otevřete. Následující příklad kódu ukazuje vytvoření vlastní vazby a programové vložení prvků vazby.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Postupy: Import kontrolních výrazů vlastních zásad](how-to-import-custom-policy-assertions.md)
