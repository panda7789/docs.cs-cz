---
title: 'Postupy: Import kontrolních výrazů vlastních zásad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: e27c6ed6508544180d8659717b700e604b0f3d3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073621"
---
# <a name="how-to-import-custom-policy-assertions"></a>Postupy: Import kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad popisují funkce a požadavky koncového bodu služby.  Klientské aplikace můžou použít kontrolní výrazy zásad v metadata služby, abyste mohli nakonfigurovat klienta vazby nebo přizpůsobit kontraktu služby koncového bodu služby.  
  
 Kontrolních výrazů vlastních zásad jsou importovány pomocí implementace <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní a předá tento objekt metadat systému nebo si zaregistrujte implementace typu v konfiguračním souboru aplikace.  Implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní musí poskytovat konstruktor default.  
  
### <a name="to-import-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
  
1.  Implementace <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní na třídě. Podívejte se na následující postupy.  
  
2.  Vložit vlastní zásady pro import buď podle:  
  
3.  Použití konfiguračního souboru. Podívejte se na následující postupy.  
  
4.  Použití konfiguračního souboru s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Podívejte se na následující postupy.  
  
5.  Programově vkládání programu pro import zásady. Podívejte se na následující postupy.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>K implementaci rozhraní System.ServiceModel.Description.IPolicyImportExtension u jakékoli třídy  
  
1.  V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodu, pro každé zásady předmětu, který vás zajímá, najít kontrolní výrazy zásad, které chcete importovat voláním příslušné metody (v závislosti na rozsahu výrazu, který chcete, aby) na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> předán objekt Metoda. Následující příklad kódu ukazuje, jak používat <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metody pro vyhledání vlastních zásad pro kontrolní výraz a odebrat z kolekce v jednom kroku. Pokud používáte metodu odebrat vyhledat a odebrat kontrolního výrazu, není nutné k provedení kroku 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  Zpracování kontrolních výrazů zásad. Všimněte si, že není normalizovat systému zásad vnořené zásady a `wsp:optional`. Tyto konstruktory musí zpracovat v implementaci rozšíření importu zásady.  
  
3.  Provedení vlastní nastavení pro vazby nebo kontrakt, který podporuje funkce nebo požadavek určený kontrolního výrazu zásad. Kontrolní výrazy obvykle signalizují, že vazba vyžaduje konkrétní konfiguraci nebo element konkrétní vazby. Proveďte tyto úpravy, díky přístupu <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> vlastnost. Další kontrolní výrazy vyžadují úpravě kontrakt.  Můžete používat a upravit pomocí kontraktu <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> vlastnost.  Všimněte si, že vaše zásady programu pro import může volána více než jednou pro stejný kontrakt a vazby, ale nepovede alternativy jiné zásady importu zásad alternativu. Váš kód by měl být odolné vůči tomuto chování.  
  
4.  Kontrolní výraz vlastní zásady pro odebrání z kolekce kontrolní výraz. Pokud nebude odstraněn kontrolního výrazu Windows Communication Foundation (WCF) předpokládá, že import zásady nebylo úspěšné a neprovede import přidružené vazby. Pokud jste použili <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metody pro vyhledání vlastních zásad pro kontrolní výraz a odebrat z kolekce v jednom kroku není nutné k provedení tohoto kroku.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Vložení vlastních zásad pro import do metadat systému je používán konfigurační soubor  
  
1.  Přidat typ programu pro import, který má `<extensions>` element v rámci [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) prvku v souboru konfigurace klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  V klientské aplikaci používat <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> řešení je automaticky vyvolána metadata a tabulkách.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Vložení vlastních zásad pro import do metadat systému pomocí Svcutil.exe  
  
1.  Přidat typ programu pro import, který má `<extensions>` element v rámci [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) element v konfiguračním souboru Svcutil.exe.config. Můžete také bodu Svcutil.exe k načtení programu pro import typů zásad zaregistrovaný v jiné konfiguraci souboru s použitím `/svcutilConfig` možnost.  
  
2.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) importovat metadata a tabulkách je vyvolán automaticky.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Vložení vlastních zásad pro import do systému metadat prostřednictvím kódu programu  
  
1.  Přidat import do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> vlastnosti (například pokud použijete <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) před importem metadata.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
