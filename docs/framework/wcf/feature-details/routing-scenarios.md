---
title: Scénáře směrování
ms.date: 03/30/2017
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: fa5d588211cfe40cde9e9db3161a931e3287cd39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223824"
---
# <a name="routing-scenarios"></a>Scénáře směrování
Směrovací služba je vysoce přizpůsobitelné, může být obtížné navrhnout efektivní logiku směrování při vytváření nové konfigurace od začátku.  Existují však několik běžných scénářů, které následují většina konfigurací směrovací služby. Zatímco tyto scénáře se nemusí vztahovat přímo na konkrétní konfiguraci, pochopení, jak lze konfigurovat směrovací služba pro zpracování těchto scénářů bude pomoc při Princip služby směrování.  
  
## <a name="common-scenarios"></a>Obvyklé scénáře  
 Základní použití směrovací služba je agregovat více cílové koncové body a snížit počet koncových bodů, které jsou vystaveny pro klientské aplikace a pak pomocí filtry zpráv pro každou zprávu směrování do správné cíl. Zprávy mohou být směrována na základě fyzické nebo logické zpracování požadavků, jako je například typ zprávy, které musí být zpracovány určité služby, nebo na základě libovolného obchodních potřeb, jako je například poskytnutí prioritu zpracování zprávy z konkrétního zdroje. V následující tabulce jsou uvedeny některé obvyklé scénáře a při jejich výskytu:  
  
|Scénář|Kdy použít|  
|--------------|--------------|  
|Správa verzí služby|Můžete potřebovat pro podporu více verzí služby nebo může v budoucnu nasazení aktualizace služby|  
|Vytvoření oddílů dat služby|Služba musí oddílů napříč více hostiteli|  
|Dynamická aktualizace|Je nutné překonfigurovat dynamicky logiku směrování za běhu pro zpracování Změna nasazení služby|  
|Vícesměrové vysílání|Jednu zprávu je nutné odeslat do více koncových bodů|  
|Protokol přemostění|Příjem zpráv jeden přenosový protokol a cílový koncový bod používá jiný protokol|  
|Zpracování chyb|Je potřeba zadat odolnost výpadky sítě nebo selhání komunikace|  
  
> [!NOTE]
>  Přestože mnoho scénářů zobrazí jsou specifické pro určité obchodní potřeby nebo požadavků na zpracování, plánování pro podporu dynamické aktualizace a využití zpracování chyb můžete často považovat za osvědčených postupů umožňují upravit logiku směrování za běhu a zotavení z chyb při přechodných síťových a komunikace.  
  
### <a name="service-versioning"></a>Verze služby  
 Při zavádění nové verze služby, musí často zachovat předchozí verze, dokud všichni klienti přešla na novou službu. To je zvlášť zásadní v případě, že služba je dlouho běžící proces, který zabere dny, týdny nebo dokonce měsíce. Obvykle vyžaduje implementace novou adresu koncového bodu pro novou službu a přitom původní koncový bod pro předchozí verze.  
  
 S použitím služby směrování, můžete zveřejnit jeden koncový bod pro příjem zpráv z klientských aplikací a pak směrovat na správné služby verzi na základě obsahu zpráv každou zprávu. Základní implementaci zahrnuje přidání vlastní hlavičky zprávy, která určuje verzi služby, který je zprávu zpracovat. Směrovací služba můžete použít XPathMessageFilter ke kontrole přítomnosti vlastní hlavičce každou zprávu a směrování zprávy do příslušné cílové koncového bodu.  
  
 Postup použitý k vytvoření konfigurace správy verzí služby najdete v tématu [How To: Správa verzí služby](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>Vytvoření oddílů dat služby  
 Když navrhujete distribuované prostředí, je často žádoucí rozložit zatížení mezi více počítačů za účelem poskytnutí vysoké dostupnosti, snížení zatížení na jednotlivých počítačích, nebo k poskytování prostředků vyhrazených pro určitou podmnožinu zpráv. Zatímco služba Směrování nenahrazuje vyhrazené řešení vyrovnávání zatížení, schopnost provést směrování obsahu na základě je možné pro směrování zpráv v opačném případě podobné určitým příjemcům. Například může mít požadavek na zpracování zpráv z konkrétního klienta nezávisle na zprávy přijaté z jiných klientů.  
  
 Postup použitý k vytvoření datové služby dělení konfigurace najdete v tématu [How To: Vytvoření oddílů dat služby](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Dynamické směrování  
 Často je žádoucí, aby změny konfigurace směrování splnit měnící se potřeby organizace, jako je například přidávání trasu na novější verzi služby, změnou kritérií směrování nebo změna koncového bodu cílové konkrétní zprávu, která filtr přesměruje. Směrovací služba umožňuje udělat prostřednictvím <xref:System.ServiceModel.Routing.RoutingExtension>, což vám umožňuje poskytovat nová konfigurace RoutingConfiguration za běhu. Nová konfigurace projeví se okamžitě, ale pouze ovlivňuje všechny nové relace zpracovaných službou směrování.  
  
 Postup používaný k implementaci dynamického směrování najdete v tématu [How To: Dynamická aktualizace](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md).
  
### <a name="multicast"></a>Vícesměrové vysílání  
 Při směrování zpráv, obvykle můžete směrování každou zprávu do koncového bodu konkrétní cílové.  Však může čas od času potřeba směrovat kopie zprávy na víc cílové koncové body. Chcete-li provést směrování vícesměrového vysílání, musí být splněné následující podmínky:  
  
-   Tvar kanálu nesmí být požadavek odpověď (i když může být jednosměrné nebo obousměrné,) vzhledem k tomu, že požadavek odpověď, určuje, že pouze jednu odpověď lze přijímat pomocí klientské aplikace v odpovědi na požadavek.  
  
-   Několik filtrů musí vracet **true** při vyhodnocování zprávy.  
  
 Pokud jsou tyto podmínky splněny, každý cílový koncový bod, který je přidružený filtr, který vrací hodnotu true, obdrží kopii zprávy.  
  
### <a name="protocol-bridging"></a>Protokol přemostění  
 Při směrování zpráv mezi rozdílných protokolů SOAP, směrovací služba používá rozhraní API WCF převést zprávy z jednoho protokolu na druhý. K tomu dojde automaticky při vystavený koncových bodů služby pomocí směrovací služba jiného protokolu než koncových bodů klienta, které zprávy jsou směrovány na. Je možné toto chování zakázat, pokud nejsou protokoly používá standardní; ale musíte pak zadat vlastní přemostění kódu.
  
### <a name="error-handling"></a>Zpracování chyb  
 V distribuovaném prostředí není nic neobvyklého, když dojde k selhání přechodné síťové nebo komunikace. Bez zprostředkující služby, jako je například služba Směrování zatížení zpracovávat takové chyby klesne na klientské aplikaci. Pokud klientská aplikace neobsahuje konkrétní logiku pro opakování v případě sítě nebo selhání komunikace a znalosti o alternativních umístění, uživatel může dojít scénáře, ve kterém zpráva musí být předloženy více než jednou předtím, než je úspěšně zpracovává cílové služby. To může vést k jejich nespokojenost zákazníka s aplikací, protože to může být vnímané jako nespolehlivé.  
  
 Směrovací služba se pokusí napravit tento scénář tím, že poskytuje robustní Chyba funkce zpracování zprávy, které dojde k síti nebo chyby týkající se komunikace. Vytvořením seznamu možných cílové koncové body a tento seznam přidružení každý filtr zpráv, odebrat jediný bod selhání vzniklé v souvislosti s pouze jeden možný cíl. V případě selhání směrovací služba se pokusí doručit zprávu další koncový bod v seznamu, dokud nebyly dodány zprávy, dojde k selhání bez komunikace, nebo všechny koncové body byly vyčerpány.  
  
 Postup slouží ke konfiguraci zpracování chyb najdete v tématu [How To: Zpracování chyb](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md).
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Verze služby](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Postupy: Vytvoření oddílů dat služby](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Postupy: Dynamická aktualizace](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Postupy: Zpracování chyb](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Viz také:

- [Směrování – úvod](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
