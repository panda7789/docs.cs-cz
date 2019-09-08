---
title: 'Postupy: Import kontrolních výrazů vlastních zásad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: 4510eac2d9c1b3bb64420b0678b3a47a90887188
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795619"
---
# <a name="how-to-import-custom-policy-assertions"></a>Postupy: Import kontrolních výrazů vlastních zásad
Kontrolní výrazy zásad popisují možnosti a požadavky koncového bodu služby.  Klientské aplikace mohou použít kontrolní výrazy zásad v metadatech služby ke konfiguraci vazby klienta nebo k přizpůsobení kontraktu služby pro koncový bod služby.  
  
 Vlastní kontrolní výrazy zásad jsou importovány implementací <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní a předáním tohoto objektu do systému metadat nebo registrací typu implementace do konfiguračního souboru aplikace.  <xref:System.ServiceModel.Description.IPolicyImportExtension> Implementace rozhraní musí poskytovat konstruktor bez parametrů.  
  
### <a name="to-import-custom-policy-assertions"></a>Import kontrolních výrazů vlastních zásad  
  
1. Implementujte <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní pro třídu. Projděte si následující postupy.  
  
2. Vložte vlastní dovozce zásad podle těchto údajů:  
  
3. Pomocí konfiguračního souboru. Projděte si následující postupy.  
  
4. Pomocí konfiguračního souboru s [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Projděte si následující postupy.  
  
5. Vložením programu pro import zásad. Projděte si následující postupy.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Implementace rozhraní System. ServiceModel. Description. třídu IPolicyImportExtension u libovolné třídy  
  
1. V metodě pro každý předmět zásad, který vás zajímá, vyhledejte kontrolní výrazy zásad, které chcete importovat, voláním příslušné metody (v závislosti na rozsahu požadovaného kontrolního výrazu) <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> na objektu předaného do <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> Metoda. Následující příklad kódu ukazuje, jak použít <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodu k vyhledání kontrolního výrazu vlastní zásady a jeho odebrání z kolekce v jednom kroku. Pokud použijete metodu Remove k vyhledání a odebrání kontrolního výrazu, není nutné provádět krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Zpracujte kontrolní výrazy zásad. Všimněte si, že systém zásad nenormalizuje vnořené zásady a `wsp:optional`. Tyto konstrukce musíte zpracovat v implementaci rozšíření importu zásad.  
  
3. Proveďte vlastní nastavení vazby nebo kontraktu, který podporuje schopnost nebo požadavek určený kontrolním výrazem zásad. Obvykle kontrolní výrazy označují, že vazba vyžaduje konkrétní konfiguraci nebo konkrétní prvek vazby. Tyto úpravy udělejte přístupem k <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> vlastnosti. Jiné kontrolní výrazy vyžadují, abyste změnili kontrakt.  Můžete použít a upravit kontrakt pomocí <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> vlastnosti.  Všimněte si, že váš Importér zásad se může u stejné vazby a kontraktu volat víckrát, ale při neúspěšném importu alternativního řešení se nezdařila jiná alternativa zásad. Váš kód by měl být odolný vůči tomuto chování.  
  
4. Odeberte kontrolní výraz vlastní zásady z kolekce kontrolního výrazu. Pokud neodeberete kontrolní výraz Windows Communication Foundation (WCF) předpokládá, že import zásad neproběhl úspěšně a neimportuje přidruženou vazbu. Pokud jste použili <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodu pro vyhledání vlastního kontrolního výrazu zásady a jeho odebrání z kolekce v jednom kroku, nemusíte tento krok provádět.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Vložení vlastního nástroje pro import zásad do systému metadat pomocí konfiguračního souboru  
  
1. Do `<extensions>` [prvku policyImporters\<>](../../configure-apps/file-schema/wcf/policyimporters.md) elementu v konfiguračním souboru klienta přidejte typ dovozce.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2. V klientské aplikaci použijte <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> k vyřešení metadat a automatické vyvolání programu pro import.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Vložení vlastního nástroje pro import zásad do systému metadat pomocí Svcutil. exe  
  
1. Do `<extensions>` [prvku policyImporters\<>](../../configure-apps/file-schema/wcf/policyimporters.md) v konfiguračním souboru Svcutil. exe. config přidejte typ dovozce. Pomocí `/svcutilConfig` možnosti můžete také odkazovat na Svcutil. exe a načíst typy pro import zásad zaregistrované v jiném konfiguračním souboru.  
  
2. Pomocí nástroje pro dopředné metadata [(Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) můžete importovat metadata a automaticky vyvolávat import.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Programové vložení vlastního nástroje pro import zásad do systému metadat  
  
1. Přidejte import do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> vlastnosti (například pokud <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>používáte) před importem metadat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozšíření systému metadat](extending-the-metadata-system.md)
