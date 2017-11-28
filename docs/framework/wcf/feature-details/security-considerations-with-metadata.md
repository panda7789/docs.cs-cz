---
title: "Informace o zabezpečení pro metadata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 75191aa28be76da549d38403c4a6f019c6f54bc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-considerations-with-metadata"></a>Informace o zabezpečení pro metadata
Když pomocí metadat funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], vezměte v úvahu bezpečnostních důsledcích publikování, načítání a pomocí služby metadat.  
  
## <a name="when-to-publish-metadata"></a>Při publikování metadat  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby nepublikujte metadata ve výchozím nastavení. Metadata pro publikování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby je potřeba explicitně povolit publikování metadat přidáním koncové body metadat do služby (najdete v části [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Opouštění publikování metadat zakázána snižuje prostor pro útoky u služby a snižuje riziko zpřístupnění neúmyslnému informací. Ne všechny služby musíte publikovat metadat. Pokud nemáte publikování metadat, zvažte, ponechejte vypnutý. Všimněte si, že stále mohou generovat kód pro metadata a klienta přímo z vaší služby sestavení s využitím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí Svcutil.exe pro export metadat, najdete v tématu [postupy: použití Svcutil.exe pro Export metadat z zkompilovat kódu služby](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikování metadat pomocí zabezpečené vazby  
 Výchozí metadat vazby, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje zabezpečení a umožňují anonymní přístup k metadatům. Metadata služby, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] publikuje služby obsahuje podrobný popis týkající se služby a mohou už úmyslně nebo náhodně obsahovat citlivé informace. Metadata služby může například obsahovat informace o operacích infrastruktury, který není určen pro veřejně všesměrového vysílání. Metadata služby ochrany před neoprávněným přístupem, můžete vytvořit vazbu zabezpečení pro svůj koncový bod metadat. Koncové body metadat reagovat na požadavky HTTP/GET, které vám pomůže zabezpečit metadata vrstvy SSL (Secure Sockets). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Zabezpečení koncových bodů metadat taky poskytuje způsob, jak žadatelů o bezpečně načítat metadata služby bez riziko zneužití nebo falšování identity.  
  
## <a name="using-only-trusted-metadata"></a>Používání jenom důvěryhodných metadat  
 Metadata služby můžete automaticky vytvořit běhu součásti požadované pro volání služby. Můžete také použít metadata v době návrhu vyvíjet aplikace klienta nebo v době běhu a dynamicky aktualizovat vazby klient používá k volání služby.  
  
 Metadata služby můžete manipulováno nebo maskování Pokud načteny nezabezpečeným způsobem. Zmanipulovanou metadata můžete přesměrovat vašeho klienta škodlivý služby, obsahují nastavení ohrožené zabezpečení nebo obsahovat škodlivý struktury XML. Metadata dokumentů mohou být velké a často se uloží do systému souborů. K ochraně proti manipulaci a falšování identity, použijte zabezpečené vazby pro vyžádání metadata služby, pokud je k dispozici.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Pomocí bezpečné techniky pro zpracování metadat  
 Metadata služby se často načítají ze služby přes síť pomocí standardizovaných protokolů, jako je WS-MetadataExchange (MEX). Mnoho formáty metadat zahrnují odkazující na mechanismy pro odkazující na dalších metadat. <xref:System.ServiceModel.Description.MetadataExchangeClient> Typ automaticky zpracuje odkazy pro vás v dokumentech webové služby popis Language (WSDL), schématu XML a MEX dokumenty. Velikost <xref:System.ServiceModel.Description.MetadataSet> objekt vytvořený z načtené metadat je přímo úměrná <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> hodnota <xref:System.ServiceModel.Description.MetadataExchangeClient> instanci, která se používá a `MaxReceivedMessageSize` hodnotu pro vazbu, který se používá <xref:System.ServiceModel.Description.MetadataExchangeClient> instance. Nastavte tyto kvóty odpovídající hodnoty, protože závisí na vašem scénáři.  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], metadata služby zpracovávány jako XML. Při zpracování dokumentů XML, aplikace by měla chránit proti škodlivým struktury XML. Použití `XmlDictionaryReader` s příslušným kvóty při zpracování jazyka XML a také nastavit <xref:System.Xml.XmlTextReader.DtdProcessing%2A> vlastnost `Prohibit`.  
  
 Systém metadat v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšiřitelný a metadata přípony můžete být zaregistrovány v konfiguračním souboru aplikace (viz [rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Rozšíření metadat můžete spustit libovolný kód, takže byste měli chránit konfiguračním souboru aplikace pomocí řízení přístupu na příslušné seznamy ACL a zaregistrovat pouze důvěryhodné metadata rozšíření implementace.  
  
## <a name="validating-generated-clients"></a>Ověřování generovaného klientů  
 Při generování kódu klienta z metadat načíst ze zdroje, která není důvěryhodná, ověřte kód klienta vygenerovaný zajistit, že generovaného klienta je v souladu se zásadami zabezpečení vaší klientské aplikace. Zkontrolujte nastavení na vašeho klienta vazby nebo vizuálně zkontrolovat kód vygenerovaný nástroje můžete použít ověřování chování. Příklad implementace klienta, která ověřuje chování naleznete v části [ověření klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrana konfigurační soubory aplikace  
 Konfigurační soubor aplikace služby může řídit způsob a zda je publikována metadat. Je vhodné k ochraně konfiguračního souboru aplikace pomocí seznamů řízení odpovídající přístupu (ACL) zajišťující, že útočník nelze upravit taková nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
