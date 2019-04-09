---
title: Podrobnosti implementace protokolu služeb WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 3fcef8778707f2bac68755762143f4a7528f0bf1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152851"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Podrobnosti implementace protokolu služeb WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Podrobnosti implementace protokolu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Vyžaduje, že služba data, která implementuje protokol poskytnout určité minimální sadu funkcí. Tyto funkce jsou popsány v dokumentech protokol z hlediska "by" a "musíte". Ostatní volitelné funkce jsou popsány z hlediska "dne." Toto téma popisuje tyto volitelné funkce, které nejsou nyní implementovány pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Další informace najdete v tématu [dokumentace k protokolu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Podpora pro možnost dotazu $format  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokol podporuje JavaScript Notation (JSON) a informační kanály Atom, a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje `$format` možností dotazu systému, aby klient k vyžádání formát odpovědi informačního kanálu. Tuto možnost dotazu systému, pokud služba data musí přepsat hodnotu hlavičky Accept požadavku. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje vracející informační kanály Atom i JSON. Však nepodporuje výchozí implementace `$format` možnosti dotazu a pouze hodnotu hlavičky Accept používá k určení formátu odpovědi. Existují případy, kdy datové služby může potřebovat pro podporu `$format` možnosti, jako je například kdy klienti nelze nastavit hlavičku Accept dotazu. Pro podporu těchto scénářů, je třeba rozšířit datové služby pro zpracování této možnosti v identifikátoru URI. Stáhněte si můžou dodat tuto funkci do služby data [JSONP a adresy URL řídit formát podporu pro služby ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) ukázkový projekt z webu Galerie kódu na webu MSDN a jeho přidání do projektu datové služby. Tento příklad odstraní `$format` možnosti dotazu a změní hlavičky Accept pro `application/json`. Pokud zahrnete ukázka projektu a přidání `JSONPSupportBehaviorAttribute` ke svým datům třídu služby umožňuje službě pro zpracování `$format` možnosti dotazu `$format=json`. Další přizpůsobení tento ukázkový projekt je vyžadován ke zpracování také `$format=atom` nebo jiných vlastních formátů.  
  
## <a name="wcf-data-services-behaviors"></a>Chování služeb WCF Data Services  
 Následující [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] chování nejsou explicitně definované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu:  
  
### <a name="default-sorting-behavior"></a>Výchozí chování řazení  
 Pokud dotaz odeslaný do služby data obsahuje `$top` nebo `$skip` systému možnosti dotazu a nezahrnuje `$orderby` možností dotazu systému, vrácené informační kanál je seřazený podle klíčové vlastnosti ve vzestupném pořadí. Je to proto, že pořadí je potřeba zajistit správné stránkování výsledků. K tomuto účelu data service přidá výraz řazení v dotazu. K tomuto chování dochází také při zapnutém stránkování řízené serverem ve službě data. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Pro ovládání řazení vrácené informačního kanálu, měli byste zahrnout `$orderby` v dotazu identifikátoru URI.  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
