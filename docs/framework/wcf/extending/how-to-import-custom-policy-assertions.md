---
title: "Postupy: Import kontrolních výrazů vlastních zásad"
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
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3cc7eecbef66c3e4a80759912260b973d441a8a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-import-custom-policy-assertions"></a>Postupy: Import kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad jsou popsány možnosti a požadavky koncového bodu služby.  Klientské aplikace můžete použít výrazy zásad v metadata služby ke konfiguraci klienta vazby nebo k přizpůsobení kontrakt služby pro koncový bod služby.  
  
 Kontrolních výrazů vlastních zásad importují implementací <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní a předání objektu metadat systému nebo tím, že zaregistrujete implementace zadejte v konfiguračním souboru aplikace.  Implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní musíte zadat výchozí konstruktor.  
  
### <a name="to-import-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
  
1.  Implementace <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní na třídu. Postupujte podle následujících pokynů.  
  
2.  Vložit – Importér vlastní zásady buď pomocí:  
  
3.  Použití konfiguračního souboru. Postupujte podle následujících pokynů.  
  
4.  Použití konfiguračního souboru s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Postupujte podle následujících pokynů.  
  
5.  Prostřednictvím kódu programu vkládání – Importér zásad. Postupujte podle následujících pokynů.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Implementace rozhraní System.ServiceModel.Description.IPolicyImportExtension u jakékoli třídy  
  
1.  V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metoda, pro každý předmět zásad, která vás zajímá, najít výrazy zásad, které chcete importovat voláním odpovídající metodu (v závislosti na rozsahu kontrolní výraz, který chcete) na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> byl předán objekt Metoda. Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metoda vyhledat výraz vlastních zásad a jeho odebrání z kolekce v jednom kroku. Pokud používáte metodu odebrat můžete nalézt a odstranit kontrolní výraz, nemáte proveďte krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  Zpracovat výrazy zásad. Všimněte si, že zásady systému není normalizaci vnořené zásady a `wsp:optional`. Je nutné zpracovat tyto konstrukce v implementaci zásad import rozšíření.  
  
3.  Proveďte vlastní vazby nebo kontrakt, který podporuje schopnosti nebo požadavek určeného výraz zásad. Kontrolní výrazy obvykle označují, že vazba vyžaduje konkrétní konfigurací nebo prvku konkrétní vazby. Proveďte tyto úpravy přímým přístupem <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> vlastnost. Další kontrolní výrazy vyžadují, že upravíte kontrakt.  Můžete používat a upravit pomocí kontrakt <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> vlastnost.  Všimněte si, že vaše zásady – Importér může získat volat vícekrát pro stejnou vazbu a kontrakt, ale jinou zásadu alternativy, pokud Import zásady alternativní selže. Váš kód by měl být odolné vůči toto chování.  
  
4.  Kontrolní výraz vlastní zásady pro odebrání z kolekce kontrolní výraz. Pokud neodeberete kontrolní výraz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] předpokládá, že import zásady nebylo úspěšné a neimportuje přidružené vazby. Pokud jste použili <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metoda vyhledat výraz vlastních zásad a jeho odebrání z kolekce v jednom kroku není nutné k provedení tohoto kroku.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Program pro import vlastních zásad pro vložení do metadat systému pomocí konfiguračního souboru  
  
1.  Přidat – Importér typ, který má `<extensions>` element uvnitř [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) element v souboru konfigurace klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  V aplikaci klienta použít <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> řešení, se automaticky vyvolá metadata a program pro import.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Program pro import vlastních zásad pro vložení do systému metadat pomocí Svcutil.exe  
  
1.  Přidat – Importér typ, který má `<extensions>` element uvnitř [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) element v konfiguračním souboru Svcutil.exe.config. Můžete také bodu Svcutil.exe načíst zásady typů – Importér zaregistrováno v různých konfiguračním souboru pomocí `/svcutilConfig` možnost.  
  
2.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) importovat metadata a – Importér vyvolán automaticky.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Vložení vlastní zásady – Importér do systém metadat prostřednictvím kódu programu  
  
1.  Přidat – Importér k <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> vlastnosti (například pokud používáte <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) před importem metadata.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 [Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
