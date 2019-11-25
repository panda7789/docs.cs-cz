---
title: Podrobnosti implementace protokolu služeb WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 10a330fd6f6f73ffc7e812e0a9012ec20c83861d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975044"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Podrobnosti implementace protokolu služeb WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Podrobnosti implementace protokolu OData  
 Protokol OData (Open Data Protocol) vyžaduje, aby datová služba, která implementuje protokol, poskytovala určitou minimální sadu funkcí. Tyto funkce jsou popsány v dokumentu protokolu ve smyslu "by měly" a "musí být". Další volitelné funkce jsou popsány v tématu "květen." Toto téma popisuje tyto volitelné funkce, které nejsou aktuálně implementovány nástrojem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Další informace najdete v [dokumentaci k protokolu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Podpora pro možnost dotazu $format  
 Protokol OData podporuje i kanály typu JavaScript (JSON) i Atom a služba OData poskytuje možnost dotazování `$format` systému, která klientovi umožní požádat o formát kanálu odpovědí. Tato možnost systémového dotazu, pokud je podporována datovou službou, musí přepsat hodnotu hlavičky Accept žádosti. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje vracení kanálů JSON a Atom. Výchozí implementace však nepodporuje možnost dotazu `$format` a používá pouze hodnotu hlavičky Accept k určení formátu odpovědi. Existují případy, kdy datová služba může potřebovat podporu `$format`ho dotazu, například když klienti nemohou nastavit hlavičku Accept. Pro podporu těchto scénářů je potřeba, abyste rozšířili svou datovou službu, abyste tuto možnost v identifikátoru URI zpracovali. Tuto funkci můžete do datové služby přidat stažením [podpory formátu JSONP a adresy URL pro ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) ukázkového projektu z webu Galerie kódu na webu MSDN a jeho přidáním do projektu datové služby. Tato ukázka odebere možnost dotazu `$format` a změní hlavičku Accept na `application/json`. Pokud zahrnete ukázkový projekt a přidáte `JSONPSupportBehaviorAttribute` do vaší třídy datové služby, umožníte službě zpracovat možnost dotazu `$format` `$format=json`. Další přizpůsobení tohoto ukázkového projektu se vyžaduje také pro zpracování `$format=atom` nebo jiných vlastních formátů.  
  
## <a name="wcf-data-services-behaviors"></a>Chování WCF Data Services  
 Následující chování [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nejsou explicitně definovány protokolem OData:  
  
### <a name="default-sorting-behavior"></a>Výchozí chování při řazení  
 Pokud požadavek na dotaz, který je odeslán do datové služby, zahrnuje možnost dotazování `$top` nebo `$skip` a neobsahuje možnost dotazování systému `$orderby`, vrácený kanál se seřadí podle vlastností klíče ve vzestupném pořadí. Důvodem je to, že k zajištění správného stránkování výsledků je vyžadováno řazení. K tomu datová služba přidá do dotazu výraz řazení. K tomuto chování dochází také v případě, že je v datové službě povolené stránkování řízené serverem. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Chcete-li řídit řazení vráceného informačního kanálu, měli byste zahrnout `$orderby` do identifikátoru URI dotazu.  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
