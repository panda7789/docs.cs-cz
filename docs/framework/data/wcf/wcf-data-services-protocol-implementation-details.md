---
title: Podrobnosti implementace protokolu služeb WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1cd4204d9e1626ac45bccf3954fdaf1c156af7f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779653"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Podrobnosti implementace protokolu služeb WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Podrobnosti implementace protokolu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Vyžaduje, aby datová služba, která implementuje protokol, poskytovala určitou minimální sadu funkcí. Tyto funkce jsou popsány v dokumentu protokolu ve smyslu "by měly" a "musí být". Další volitelné funkce jsou popsány v tématu "květen." Toto téma popisuje tyto volitelné funkce, které nejsou aktuálně implementovány nástrojem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Další informace najdete v [dokumentaci k protokolu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Podpora pro možnost dotazu $format  
 Protokol podporuje jak kanály JavaScript (JSON), tak i kanály Atom a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje `$format` možnost dotazování systému, která klientovi umožní požádat o formát kanálu odpovědí. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Tato možnost systémového dotazu, pokud je podporována datovou službou, musí přepsat hodnotu hlavičky Accept žádosti. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje vracení kanálů JSON a Atom. Výchozí implementace však nepodporuje `$format` možnost dotazu a používá pouze hodnotu hlavičky Accept k určení formátu odpovědi. Existují případy, kdy vaše datová služba může potřebovat podporu `$format` dotazu, například když klienti nemohou nastavit hlavičku Accept. Pro podporu těchto scénářů je potřeba, abyste rozšířili svou datovou službu, abyste tuto možnost v identifikátoru URI zpracovali. Tuto funkci můžete do datové služby přidat stažením [podpory formátu JSONP a adresy URL pro ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) ukázkového projektu z webu Galerie kódu na webu MSDN a jeho přidáním do projektu datové služby. Tato ukázka odebere `$format` možnost dotazu a změní hlavičku Accept na `application/json`. Pokud zahrnete vzorový projekt a přidáte `JSONPSupportBehaviorAttribute` do své třídy datové služby, umožníte službě `$format` zpracování možnosti `$format=json`dotazu. Další přizpůsobení tohoto ukázkového projektu je nutné také pro zpracování `$format=atom` nebo jiné vlastní formáty.  
  
## <a name="wcf-data-services-behaviors"></a>Chování WCF Data Services  
 Následující [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] chování nejsou explicitně definovány [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolem:  
  
### <a name="default-sorting-behavior"></a>Výchozí chování při řazení  
 Když požadavek na dotaz, který je odeslán do datové služby, obsahuje `$top` možnost `$skip` nebo dotaz na systém a nezahrnuje možnost `$orderby` dotaz na systém, vrácený kanál se seřadí podle vlastností klíče ve vzestupném pořadí. Důvodem je to, že k zajištění správného stránkování výsledků je vyžadováno řazení. K tomu datová služba přidá do dotazu výraz řazení. K tomuto chování dochází také v případě, že je v datové službě povolené stránkování řízené serverem. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Chcete-li řídit řazení vráceného informačního kanálu, měli `$orderby` byste zahrnout do identifikátoru URI dotazu.  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
