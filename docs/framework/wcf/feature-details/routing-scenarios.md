---
title: "Scénáře směrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 7ae79ad13b360a61e1d9b10f94dff5a37aae1d89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="routing-scenarios"></a>Scénáře směrování
I službu Směrování je vysoce přizpůsobitelné, může být výzvy k návrhu logiku efektivní směrování, při vytváření nové konfigurace od začátku.  Existují však několik běžných scénářů, které následují většina konfigurace služby směrování. Při těchto scénářích se přímo na konkrétní konfiguraci nemusí vztahovat, pochopení konfigurace služby směrování pro zpracování těchto scénářích se pomoci při Princip služby směrování.  
  
## <a name="common-scenarios"></a>Běžné scénáře  
 Základní způsob použití služby směrování je agregovat několik koncových bodů cílové a snížit počet koncových bodů vystavený pro klientské aplikace a pak používat filtry zpráv ke směrování každou zprávu na správnou cílovou. Zprávy mohou být směrována na základě logickou nebo fyzickou zpracování požadavků, jako je například typ zprávy, který musí být zpracovány určité služby, nebo libovolný podnikové potřeby například poskytování prioritu zpracování zprávy z konkrétního zdroje. Následující tabulka uvádí některé z následujících běžných scénářů, a když se vyskytují:  
  
|Scénář|Kdy použít|  
|--------------|--------------|  
|Správa verzí služeb|Potřebujete pro podporu více verzí služby nebo může v budoucnu nasazení služby aktualizované|  
|Vytvoření oddílů dat služby|Služba musí oddílu ve více hostitelích|  
|Dynamická aktualizace|Je nutné překonfigurovat dynamicky směrování logiku za běhu pro zpracování Změna nasazení služby|  
|Vícesměrové vysílání|Je nutné odeslat jednu zprávu několik koncových bodů|  
|Protokol přemostění|Zobrazí se zprávy jeden zajišťuje přenosový protokol a koncový bod cílové používá jiný protokol|  
|Zpracování chyb|Je třeba zadat odolnost proti výpadkům sítě a selhání komunikace|  
  
> [!NOTE]
>  Při mnoho scénářů uvedené jsou specifické pro určité obchodním potřebám nebo požadavky na zpracování, plánování podpory dynamické aktualizace a využití zpracování chyb můžete často být považován za jako nejlepší postupy jejich umožňují upravit směrování logiku za běhu a obnovit z přechodných chyb sítě a komunikace.  
  
### <a name="service-versioning"></a>Verze služby  
 Při zavádění nové verze služby, musí často zachovat předchozí verzi, dokud všichni klienti mají přešla na novou službu. To je obzvláště důležité, pokud služba je dlouhotrvající proces, který přebírá dny, týdny nebo měsíce i pro dokončení. Obvykle vyžaduje implementace nové adresa koncového bodu pro novou službu při zachování původní koncový bod pro předchozí verze.  
  
 Pomocí služby směrování můžete vystavit jeden koncový bod pro příjem zpráv z klientských aplikací a pak směrovat každou zprávu správná verze podle obsahu zprávy. Nejzákladnější implementace zahrnuje přidání vlastní hlavičky na zprávu, která označuje verzi službu, která zprávu zpracovat. Směrovací služby můžete použít XPathMessageFilter kontrolovat přítomnost Vlastní hlavička každou zprávu a směrovat zprávy do příslušné cílové koncový bod.  
  
 Postup použitý k vytvoření konfigurace správy verzí služby najdete v tématu [postupy: Správa verzí služeb](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md). Příklad použití XPathMessageFilter pro směrování zpráv podle vlastní hlavičky, najdete v článku [rozšířené filtry](../../../../docs/framework/wcf/samples/advanced-filters.md) ukázka.  
  
### <a name="service-data-partitioning"></a>Vytvoření oddílů dat služby  
 Při navrhování distribuovaném prostředí, je často žádoucí rozkládá zatížení mezi více počítači za účelem zajištění vysoké dostupnosti, snížit zatížení na jednotlivých počítačích, nebo k poskytnutí prostředků vyhrazené pro určitou dílčí sadu zpráv. Při směrovací služby nenahrazuje vyhrazené řešení vyrovnávání zatížení, jeho schopnost provádět obsahu založené na směrování lze jinak podobné zprávy trasy k určitým příjemcům. Například může mít požadavek zpracování zpráv z konkrétního klienta nezávisle na zprávy přijaté z jiných klientů.  
  
 Postup použít k vytvoření služby dat, vytváření oddílů konfigurace najdete v tématu [postupy: vytvoření oddílů dat služby](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md). Příklad použití filtrů k oddílu dat na základě adresy URL a vlastní hlavičky, najdete v článku [rozšířené filtry](../../../../docs/framework/wcf/samples/advanced-filters.md) ukázka.  
  
### <a name="dynamic-routing"></a>Dynamické směrování  
 Často je třeba upravit konfigurace směrování pro uspokojení měnícím se potřebám firmy, jako je například přidávání trasu na novější verzi služby, změna směrování kritérií nebo změna cílového koncového bodu konkrétní zprávou, která filtr směruje na. Směrovací služby umožňuje to provést prostřednictvím <xref:System.ServiceModel.Routing.RoutingExtension>, který vám umožňuje poskytovat nové RoutingConfiguration za běhu. Nová konfigurace se projeví okamžitě, ale pouze ovlivňuje všechny nové relace zpracovaných službou směrování.  
  
 Použít k implementaci dynamické směrování pokyny najdete v části [postupy: dynamická aktualizace](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md). Příklad použití dynamické směrování, najdete v článku [dynamická Rekonfigurace](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md) ukázka.  
  
### <a name="multicast"></a>Vícesměrové vysílání  
 Když směrování zpráv, obvykle můžete směrování každou zprávu do určité cílové koncového bodu.  Však může občas potřebujete směrovat kopie zprávy do více cílové koncové body. Chcete-li provést směrování vícesměrového vysílání, musí být splněné následující podmínky:  
  
-   Tvar kanálu nesmí být požadavku a odpovědi (i když může být jednosměrná nebo duplexní,) protože požadavku a odpovědi vyžaduje, aby pouze jednu odpověď lze přijímat pomocí klienta aplikace v odpovědi na požadavek.  
  
-   Více filtrů musí vracet **true** při vyhodnocování zprávy.  
  
 Pokud jsou tyto podmínky splněny, každý cílový koncový bod, který je přidružen filtr, který vrátí hodnotu true, obdrží kopii zprávy.  
  
### <a name="protocol-bridging"></a>Protokol přemostění  
 Při směrování zpráv mezi odlišné protokoly SOAP, směrování služba používá rozhraní API WCF převést zprávy z jednoho protokolu na druhý. K tomu dojde automaticky při koncové služby vystavené směrovací služby použijte jiný protokol než koncové klienta, který jsou směrovány zprávy. Je možné toto chování zakázat, pokud nejsou protokoly používá standardní; ale poté musíte zadat vlastní přemostění kódu.  
  
 . Příklad použití služby směrování zpráv mezi protokoly přeložit, naleznete v části [přemostění a zpracování chyb](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) ukázka.  
  
### <a name="error-handling"></a>Zpracování chyb  
 V distribuovaném prostředí není setkat přechodných chyb sítě nebo komunikace. Bez služby zprostředkující například směrovací služby zatížení zpracovávat takových selhání klesne na klientské aplikaci. Pokud aplikace klienta neobsahuje určitou logiku zopakujte akci v případě sítě nebo selhání komunikace a znalosti o alternativní umístění, uživatel může dojít scénáře, kde zprávu podává několikrát předtím, než je úspěšně zpracovává cílové služby. To může vést k nespokojenosti zákazníků s aplikací, protože ho může zaznamenatelného jako nespolehlivé.  
  
 Chcete-li vyřešit tento scénář tím, že poskytuje robustní chyba zpracování možnosti pro zprávy, které se síť nebo chyby týkající se komunikace pokusy o směrovací služby. Vytvoření seznamu možných cílové koncových bodů a přidružení tento seznam se každý filtr zpráv, odeberte jediný bod selhání způsobené s pouze na jeden možný cíl. V případě selhání se pokusí směrovací služby doručení zprávy do další koncového bodu v seznamu, dokud zpráva byla doručena, dojde k selhání bez komunikace, nebo byly vyčerpány všechny koncové body.  
  
 Pokyny slouží ke konfiguraci zpracování chyb, najdete v části [postupy: zpracování chyb](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md). Příklad implementace zpracování chyb, naleznete v části [přemostění a zpracování chyb](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) a [pokročilé zpracování chyb](../../../../docs/framework/wcf/samples/advanced-error-handling.md) ukázky.  
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Verze služby](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Postupy: Vytvoření oddílů dat služby](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Postupy: Dynamická aktualizace](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Postupy: Zpracování chyb](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Viz také  
 [Směrování – Úvod](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
