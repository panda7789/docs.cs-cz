---
title: Informace o zabezpečení pro metadata
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: c41ebf5c39e74932a4bade610c4e236b28444327
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601020"
---
# <a name="security-considerations-with-metadata"></a>Informace o zabezpečení pro metadata
Při použití funkcí metadat v Windows Communication Foundation (WCF) zvažte dopady zabezpečení publikování, načítání a používání metadat služby.  
  
## <a name="when-to-publish-metadata"></a>Kdy publikovat metadata  
 Služby WCF ve výchozím nastavení nepublikují metadata. Pokud chcete publikovat metadata pro službu WCF, musíte explicitně povolit publikování metadat přidáním koncových bodů metadat do vaší služby (viz [metadata publikování](publishing-metadata.md)). Vypnutí publikování metadat snižuje velikost prostoru pro útoky na vaši službu a snižuje riziko neúmyslného zpřístupnění informací. Ne všechny služby musí publikovat metadata. Pokud nepotřebujete publikovat metadata, zvažte, jestli je vypnutá. Všimněte si, že stále můžete generovat metadata a kód klienta přímo ze svých sestavení služby pomocí nástroje pro nástroj pro [metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace o použití Svcutil. exe k exportu metadat naleznete v tématu [How to: use Svcutil. exe to export metadata z zkompilovaného kódu služby](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikování metadat pomocí zabezpečené vazby  
 Výchozí vazby metadat, které poskytuje WCF, nejsou zabezpečené a umožňují anonymní přístup k metadatům. Metadata služby, která publikuje služba WCF, obsahuje podrobný popis služby a může úmyslně nebo neúmyslně obsahovat citlivé údaje. Metadata služby mohou například obsahovat informace o operacích infrastruktury, které nebyly určeny k vysílání ve veřejném provozu. Chcete-li chránit metadata služby před neoprávněným přístupem, můžete použít zabezpečenou vazbu pro koncový bod metadat. Koncové body metadat reagují na požadavky HTTP/GET, které mohou použít SSL (Secure Sockets Layer) (SSL) k zabezpečení metadat. Další informace najdete v tématu [Postup: zabezpečení koncových bodů metadat](how-to-secure-metadata-endpoints.md).  
  
 Zabezpečení koncových bodů metadat také poskytuje žadateli způsob, jak bezpečně načítat metadata služby bez rizika manipulace nebo falšování.  
  
## <a name="using-only-trusted-metadata"></a>Použití jenom důvěryhodných metadat  
 Metadata služby můžete použít k automatickému sestavení součástí modulu runtime potřebných k volání služby. Metadata v době návrhu můžete také použít k vývoji klientské aplikace nebo za běhu za účelem dynamické aktualizace vazby, kterou klient používá k volání služby.  
  
 Metadata služby můžou být úmyslně poškozená nebo mají falešná poškození, když se načítají nezabezpečeným způsobem. Úmyslně poškozená metadata mohou přesměrovat klienta na škodlivou službu, obsahovat nastavení ohrožené zabezpečení nebo obsahovat škodlivé struktury XML. Dokumenty metadat můžou být velké a často se ukládají do systému souborů. Pro zajištění ochrany proti falšování a falšování identity použijte zabezpečenou vazbu k vyžádání metadat služby, když je k dispozici.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Používání bezpečných technik pro zpracování metadat  
 Metadata služby se často načítají ze služby prostřednictvím sítě pomocí standardizovaných protokolů, jako je WS-MetadataExchange (MEX). Mnoho formátů metadat zahrnuje odkazování mechanismů, které odkazují na další metadata. <xref:System.ServiceModel.Description.MetadataExchangeClient>Typ automaticky zpracovává odkazy v dokumentech jazyka WSDL (Web Services Description Language), schématu XML a dokumentů MEX. Velikost <xref:System.ServiceModel.Description.MetadataSet> objektu vytvořeného z načtených metadat je přímo úměrná <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> hodnotě <xref:System.ServiceModel.Description.MetadataExchangeClient> používané instance a `MaxReceivedMessageSize` hodnotě vazby používané touto <xref:System.ServiceModel.Description.MetadataExchangeClient> instancí. Nastavte tyto kvóty na příslušné hodnoty podle vašeho scénáře.  
  
 V rámci WCF se metadata služby zpracovávají jako XML. Při zpracování dokumentů XML by aplikace měly chránit před škodlivými strukturami XML. Použijte <xref:System.Xml.XmlDictionaryReader> s vhodnými kvótami při zpracování XML a také nastavte <xref:System.Xml.XmlTextReader.DtdProcessing%2A> vlastnost na <xref:System.Xml.DtdProcessing.Prohibit> .  
  
 Systém metadat v technologii WCF je rozšiřitelný a rozšíření metadat lze registrovat v konfiguračním souboru aplikace (viz [rozšíření systému metadat](../extending/extending-the-metadata-system.md)). Rozšíření metadat mohou spustit libovolný kód, takže byste měli chránit konfigurační soubor aplikace pomocí příslušných seznamů řízení přístupu (ACL) a registrovat pouze implementace důvěryhodného rozšíření metadat.  
  
## <a name="validating-generated-clients"></a>Ověřování vygenerovaných klientů  
 Při generování klientského kódu z metadat načtených ze zdroje, který není důvěryhodný, ověřte generovaný klientský kód, aby se zajistilo, že vygenerovaný klient odpovídá zásadám zabezpečení vašich klientských aplikací. Můžete použít chování ověřování pro kontrolu nastavení na vazbách klientů nebo vizuálně kontrolovat kód generovaný nástroji. Příklad implementace klienta, který ověřuje chování, najdete v tématu [ověření klienta](../samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrana konfiguračních souborů aplikace  
 Konfigurační soubor aplikace služby může určovat, jak a kdy se metadata publikují. Je vhodné chránit konfigurační soubor aplikace pomocí příslušných seznamů řízení přístupu (ACL), abyste zajistili, že Útočník nemůže tato nastavení změnit.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Zabezpečené koncové body metadat](how-to-secure-metadata-endpoints.md)
- [Zabezpečení](security.md)
