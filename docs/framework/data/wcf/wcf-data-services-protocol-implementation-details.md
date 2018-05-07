---
title: Podrobnosti implementace protokolu služeb WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 82218f1f8e14c9909d8b617c66b1f18a28e4dcee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Podrobnosti implementace protokolu služeb WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Podrobnosti implementace protokolu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Vyžaduje, aby služba dat, která implementuje protokol zadali určité minimální sadu funkcí. Tyto funkce jsou popsány v dokumentech protokol z hlediska "by" a "musí." Další volitelné funkce jsou popsány z hlediska "nemusí." Toto téma popisuje tyto volitelné funkce, které nejsou implementované aktuálně [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Další informace najdete v tématu [dokumentace k protokolu OData](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Podpora pro možnost dotazu $format  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokol podporuje JavaScript Notation (JSON) a Atom informační kanály, a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje `$format` možností dotazu systému a tak dovolit klientským požádat o formát odpovědi informačního kanálu. Tuto možnost dotazu systému podporována službou data, musíte změnit hodnotu hlavičky Accept požadavku. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje vrácení Atom i JSON informačních kanálů. Však nepodporuje výchozí implementace `$format` možnost dotazu a pouze hodnotu hlavičky Accept používá k určení formátu odpovědi. Existují případy, pokud služby dat může potřebovat pro podporu `$format` dotazu možnost, například kdy klienti nelze nastavit hlavičku Accept. Pro podporu těchto scénářů, musíte rozšířit služby data pro zpracování této možnosti v identifikátoru URI. Tuto funkci můžete přidat k vaší službě data stažením [JSONP a formát adresy URL řízené podporu pro technologii ADO.NET Data Services](http://go.microsoft.com/fwlink/?LinkId=208228) ukázkový projekt z webu galerie kódů MSDN a její přidání do projektu služby data. Tato ukázka odebere `$format` možnost dotazu a změní hlavičku Accept pro `application/json`. Pokud zahrnete ukázka projektu a přidání `JSONPSupportBehaviorAttribute` ke svým datům třída služby povoluje službu pro zpracování `$format` dotazu možnost `$format=json`. Je potřeba další přizpůsobení tento ukázkový projekt zpracovávají také dříve `$format=atom` nebo dalších vlastních formátů.  
  
## <a name="wcf-data-services-behaviors"></a>Chování služeb WCF Data Services  
 Následující [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] chování nejsou výslovně definované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu:  
  
### <a name="default-sorting-behavior"></a>Výchozí chování řazení  
 Když zahrnuje požadavek dotazu, který je odešle do služby data `$top` nebo `$skip` systému možnost dotazu a nezahrnuje `$orderby` možností dotazu systému, vrácený informačního kanálu je seřazen podle vlastnosti klíče ve vzestupném pořadí. Je to proto, že řazení je potřeba zajistit správné stránkování výsledků. K tomu, přidá službu data výraz řazení pro dotaz. Toto chování se taky nastane, když je povoleno stránkování řízené serverem ve službě data. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). K řízení řazení vrácený informačního kanálu, by měla obsahovat `$orderby` v identifikátoru URI dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
