---
title: 'Postupy: Import kontrolních výrazů vlastních zásad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: ed8aae30875e3b17f65be5857c7d93af98db9b3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185559"
---
# <a name="how-to-import-custom-policy-assertions"></a>Postupy: Import kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad popisují možnosti a požadavky koncového bodu služby.  Klientské aplikace mohou použít kontrolní výrazy zásad v metadatech služby ke konfiguraci vazby klienta nebo k přizpůsobení smlouvy o poskytování služeb pro koncový bod služby.  
  
 Vlastní výrazy zásad jsou importovány <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> implementací rozhraní a předáním tohoto objektu do systému metadat nebo registrací typu implementace v konfiguračním souboru aplikace.  Implementace <xref:System.ServiceModel.Description.IPolicyImportExtension> rozhraní musí poskytnout konstruktor bez parametrů.  
  
### <a name="to-import-custom-policy-assertions"></a>Import vlastních kontrolních výrazů zásad zásad  
  
1. Implementujte <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní ve třídě. Viz následující postupy.  
  
2. Vložte importér vlastních zásad buď takto:  
  
3. Použití konfiguračního souboru. Viz následující postupy.  
  
4. Použití konfiguračního souboru s [nástrojem ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Viz následující postupy.  
  
5. Programově vkládání importér zásad. Viz následující postupy.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Implementace rozhraní System.ServiceModel.Description.IPolicyImportExtension v libovolné třídě  
  
1. V <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodě pro každý předmět zásady, který vás zajímá, najděte kontrolní výrazy zásad, které chcete importovat voláním <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> příslušné metody (v závislosti na rozsahu kontrolního výrazu, který chcete) na objekt předaný metodě. Následující příklad kódu ukazuje, <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> jak použít metodu k vyhledání vlastní výraz zásady a odebrat z kolekce v jednom kroku. Pokud použijete metodu remove k vyhledání a odebrání kontrolního výrazu, není třeba provádět krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Zpracovat kontrolní výrazy zásad. Všimněte si, že systém zásad `wsp:optional`nenormalizuje vnořené zásady a . Tyto konstrukce je nutné zpracovat v implementaci rozšíření importu zásad.  
  
3. Proveďte vlastní nastavení vazby nebo smlouvy, která podporuje schopnostnebo požadavek určený kontrolním výrazem zásady. Kontrolní výrazy obvykle označují, že vazba vyžaduje určitou konfiguraci nebo určitý prvek vazby. Proveďte tyto změny přístupem <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> k vlastnosti. Jiné kontrolní výrazy vyžadují, abyste změnili smlouvu.  Můžete přistupovat a upravovat <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> smlouvy pomocí vlastnosti.  Všimněte si, že import zásad může získat volání vícekrát pro stejnou vazbu a smlouvy, ale různé alternativy zásad, pokud se nezdaří import alternativy zásad. Váš kód by měl být odolný vůči tomuto chování.  
  
4. Odeberte vlastní výraz zásady z kolekce kontrolních výrazů. Pokud neodeberete kontrolní výraz Windows Communication Foundation (WCF) předpokládá, že import zásad byl neúspěšný a neimportuje přidružené vazby. Pokud jste <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> použili metodu k vyhledání vlastní zásady kontrolní výraz a odebrat z kolekce v jednom kroku není nutné provést tento krok.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Vložení vlastního importu zásad do systému metadat pomocí konfiguračního souboru  
  
1. Přidejte typ importu `<extensions>` do prvku uvnitř [ \<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) prvek v konfiguračním souboru klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. V klientské aplikaci <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> použijte nebo vyřešit metadata a importér je vyvolána automaticky.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Vložení vlastního importu zásad do systému metadat pomocí programu Svcutil.exe  
  
1. Přidejte typ importu do `<extensions>` prvku uvnitř [ \<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) prvek v konfiguračním souboru Svcutil.exe.config. Můžete také bod Svcutil.exe načíst typy importu zásad registrované `/svcutilConfig` v jiném konfiguračním souboru pomocí možnosti.  
  
2. Pomocí [nástroje ServiceModel Metadata Utility Tool Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) importujte metadata a importér je vyvolán automaticky.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Chcete-li vložit vlastní zásady importu do systému metadat programově  
  
1. Přidejte importér do vlastnosti <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> (například <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>pokud používáte ) před importem metadat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozšíření systému metadat](extending-the-metadata-system.md)
