---
title: Informace o zabezpečení pro metadata
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b8028b27e721e19a5fc01887e4095218d0e14436
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498540"
---
# <a name="security-considerations-with-metadata"></a>Informace o zabezpečení pro metadata
Pokud používáte metadata funkce v systému Windows Communication Foundation (WCF), zvažte bezpečnostních důsledcích publikování, načítání a pomocí služby metadat.  
  
## <a name="when-to-publish-metadata"></a>Při publikování metadat  
 Služby WCF nepublikujte metadata ve výchozím nastavení. K publikování metadat služby WCF je potřeba explicitně povolit publikování metadat přidáním koncové body metadat do služby (viz [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Opouštění publikování metadat zakázána snižuje prostor pro útoky u služby a snižuje riziko zpřístupnění neúmyslnému informací. Ne všechny služby musíte publikovat metadat. Pokud nemáte publikování metadat, zvažte, ponechejte vypnutý. Všimněte si, že stále mohou generovat kód pro metadata a klienta přímo z vaší služby sestavení s využitím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace o používání Svcutil.exe pro export metadat najdete v tématu [postupy: použití Svcutil.exe pro Export metadat z zkompilovat kódu služby](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikování metadat pomocí zabezpečené vazby  
 Výchozí metadat vazby, které WCF poskytuje nejsou zabezpečené a povolení anonymního přístupu k metadatům. Metadata služby, který publikuje služby WCF obsahuje podrobný popis týkající se služby a může úmyslně nebo neúmyslně obsahovat citlivé informace. Metadata služby může například obsahovat informace o operacích infrastruktury, který není určen pro veřejně všesměrového vysílání. Metadata služby ochrany před neoprávněným přístupem, můžete vytvořit vazbu zabezpečení pro svůj koncový bod metadat. Koncové body metadat reagovat na požadavky HTTP/GET, které vám pomůže zabezpečit metadata vrstvy SSL (Secure Sockets). Další informace najdete v tématu [postupy: zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Zabezpečení koncových bodů metadat taky poskytuje způsob, jak žadatelů o bezpečně načítat metadata služby bez riziko zneužití nebo falšování identity.  
  
## <a name="using-only-trusted-metadata"></a>Používání jenom důvěryhodných metadat  
 Metadata služby můžete automaticky vytvořit běhu součásti požadované pro volání služby. Můžete také použít metadata v době návrhu vyvíjet aplikace klienta nebo v době běhu a dynamicky aktualizovat vazby klient používá k volání služby.  
  
 Metadata služby můžete manipulováno nebo maskování Pokud načteny nezabezpečeným způsobem. Zmanipulovanou metadata můžete přesměrovat vašeho klienta škodlivý služby, obsahují nastavení ohrožené zabezpečení nebo obsahovat škodlivý struktury XML. Metadata dokumentů mohou být velké a často se uloží do systému souborů. K ochraně proti manipulaci a falšování identity, použijte zabezpečené vazby pro vyžádání metadata služby, pokud je k dispozici.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Pomocí bezpečné techniky pro zpracování metadat  
 Metadata služby se často načítají ze služby přes síť pomocí standardizovaných protokolů, jako je WS-MetadataExchange (MEX). Mnoho formáty metadat zahrnují odkazující na mechanismy pro odkazující na dalších metadat. <xref:System.ServiceModel.Description.MetadataExchangeClient> Typ automaticky zpracuje odkazy pro vás v dokumentech webové služby popis Language (WSDL), schématu XML a MEX dokumenty. Velikost <xref:System.ServiceModel.Description.MetadataSet> objekt vytvořený z načtené metadat je přímo úměrná <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> hodnota <xref:System.ServiceModel.Description.MetadataExchangeClient> instanci, která se používá a `MaxReceivedMessageSize` hodnotu pro vazbu, který se používá <xref:System.ServiceModel.Description.MetadataExchangeClient> instance. Nastavte tyto kvóty odpovídající hodnoty, protože závisí na vašem scénáři.  
  
 Ve službě WCF metadata služby zpracovávány jako XML. Při zpracování dokumentů XML, aplikace by měla chránit proti škodlivým struktury XML. Použití `XmlDictionaryReader` s příslušným kvóty při zpracování jazyka XML a také nastavit <xref:System.Xml.XmlTextReader.DtdProcessing%2A> vlastnost `Prohibit`.  
  
 Systém metadat ve WCF je rozšiřitelný a metadata přípony můžete být zaregistrovány v konfiguračním souboru aplikace (viz [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Rozšíření metadat můžete spustit libovolný kód, takže byste měli chránit konfiguračním souboru aplikace pomocí řízení přístupu na příslušné seznamy ACL a zaregistrovat pouze důvěryhodné metadata rozšíření implementace.  
  
## <a name="validating-generated-clients"></a>Ověřování generovaného klientů  
 Při generování kódu klienta z metadat načíst ze zdroje, která není důvěryhodná, ověřte kód klienta vygenerovaný zajistit, že generovaného klienta je v souladu se zásadami zabezpečení vaší klientské aplikace. Zkontrolujte nastavení na vašeho klienta vazby nebo vizuálně zkontrolovat kód vygenerovaný nástroje můžete použít ověřování chování. Příklad implementace klienta, která ověřuje chování naleznete v části [ověření klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrana konfigurační soubory aplikace  
 Konfigurační soubor aplikace služby může řídit způsob a zda je publikována metadat. Je vhodné k ochraně konfiguračního souboru aplikace pomocí seznamů řízení odpovídající přístupu (ACL) zajišťující, že útočník nelze upravit taková nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
