---
title: Informace o zabezpečení pro metadata
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: 4afa040744b1b1a8a25addb954d5785436899434
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187592"
---
# <a name="security-considerations-with-metadata"></a>Informace o zabezpečení pro metadata
Při použití funkce metadat Windows Communication Foundation (WCF), vezměte v úvahu bezpečnostních důsledcích publikování, načítání a používání metadat služby.  
  
## <a name="when-to-publish-metadata"></a>Při publikování metadat  
 Služby WCF nepublikujte metadata ve výchozím nastavení. Publikování metadat služby WCF musíte výslovně povolit publikování metadat tak, že přidáte koncové body metadat k vaší službě (viz [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Opuštění publikování metadat zakázané snižuje útok pro vaši službu a snižuje riziko nechtěné informacím. Ne všechny služby musí publikování metadat. Pokud nemáte měla být zveřejněna metadata, zvažte, se v něm vypnuté. Všimněte si, že stále může generovat metadata a klienta kód přímo z vaší služby sestavení pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace o použití Svcutil.exe pro export metadat najdete v tématu [postupy: použití Svcutil.exe pro Export metadat z kompilaci kódu služby](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikování metadat pomocí zabezpečené vazby  
 Výchozí vazby metadat, které poskytuje WCF nejsou zabezpečené a povolení anonymního přístupu k metadatům. Metadata služby, který publikuje služba WCF obsahuje podrobný popis týkající se služby a mohou úmyslně nebo neúmyslně obsahovat citlivé informace. Metadata služby může například obsahovat informace o operacích infrastruktury, nezamýšlených veřejně vysílání. Metadata služby ochrany před neoprávněným přístupem, můžete použít zabezpečené vazby pro koncový bod metadat. Koncové body metadat reagovat na požadavky HTTP/GET, které slouží k zabezpečení metadata vrstvy SSL (Secure Sockets). Další informace najdete v tématu [postupy: zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Zabezpečení koncových bodů metadat také poskytuje způsob, jak bezpečně načíst metadata služby bez rizika, manipulaci nebo falšování identity žadatele.  
  
## <a name="using-only-trusted-metadata"></a>Používání jenom důvěryhodných metadat  
 Metadata služby můžete použít k vytvoření automaticky za běhu komponenty potřebné k vyvolání služby. Můžete také použít metadat v době návrhu k vývoji aplikace klienta nebo za běhu dynamicky aktualizovat vazbu klient používá k volání služby.  
  
 Metadata služby může být úmyslně poškodit nebo falešné při načítání nezabezpečeným způsobem. Zmanipulovanou metadata mohou přesměrování klienta na škodlivé služby, obsahují nastavení ohrožené zabezpečení nebo obsahovat škodlivé struktury XML. Metadata dokumentů mohou být velké a často se uloží do systému souborů. K ochraně proti manipulaci a falšování identity, použijte zabezpečené vazby žádat o service metadata, když je k dispozici.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Bezpečné technik zpracování metadat  
 Metadata služby se často načítají ze služby přes síť pomocí standardizovaných protokolů, jako je WS-MetadataExchange (MEX). Mnoho metadat formáty odkazuje na mechanismy pro odkazující na další metadata. <xref:System.ServiceModel.Description.MetadataExchangeClient> Typ automaticky zpracovává odkazy pro vás v dokumenty služby popis jazyka WSDL (Web), schématu XML a MEX dokumenty. Velikost <xref:System.ServiceModel.Description.MetadataSet> objekt vytvořený z načtených metadat je přímo úměrná <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> hodnota <xref:System.ServiceModel.Description.MetadataExchangeClient> instanci, která se používá a `MaxReceivedMessageSize` hodnota pro vazbu, která používá <xref:System.ServiceModel.Description.MetadataExchangeClient> instance. Nastavte tyto kvóty na odpovídající hodnoty, protože závisí váš scénář.  
  
 Ve službě WCF metadata služby zpracování formátu XML. Při zpracování dokumentů XML, aplikace by měla chránit proti škodlivým struktury XML. Použití `XmlDictionaryReader` s příslušným kvóty při zpracování jazyka XML a také nastavit <xref:System.Xml.XmlTextReader.DtdProcessing%2A> vlastnost `Prohibit`.  
  
 Metadata systému ve službě WCF je možné rozšířit a metadata rozšíření může být registrováno v konfiguračním souboru aplikace (viz [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Metadata rozšíření může spustit libovolný kód, takže by měla chránit váš konfigurační soubor aplikace pomocí řízení přístupu na příslušné seznamy ACL a zaregistrovat jenom důvěryhodné metadata rozšíření implementace.  
  
## <a name="validating-generated-clients"></a>Ověřuje se vygenerovaný klientů  
 Při generování kódu klienta z metadat načíst ze zdroje, která není důvěryhodná, ověřování kódu generovaného klienta k zajištění, že generovaného klienta v souladu se zásadami zabezpečení vaší klientské aplikace. Ověřování chování slouží k nastavení vašeho klienta vazby nebo vizuálně zkoumat kód vygenerovaný nástroje. Příklad implementace, které ověří chování klienta najdete v části [ověřování na straně klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrana konfigurační soubory aplikace  
 Konfigurační soubor aplikace služby mohou řídit jak a v případě publikování metadat. Je vhodné pro ochranu pomocí seznamů řízení odpovídající přístupu (ACL) se ujistěte se, že útočník nelze změnit tato nastavení konfiguračního souboru aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
