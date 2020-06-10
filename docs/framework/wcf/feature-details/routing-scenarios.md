---
title: Scénáře směrování
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: 455a6e42aea064d48846994b4e729b90667bc8e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590498"
---
# <a name="routing-scenarios"></a>Scénáře směrování
I když je služba Směrování vysoce přizpůsobitelná, může být při vytváření nové konfigurace od začátku výzvou pro návrh efektivní logiky směrování.  Existuje však několik běžných scénářů, které následují konfigurace služby směrování. I když se tyto scénáře nemusí vztahovat přímo na konkrétní konfiguraci, porozumět tomu, jak se dá služba Směrování nakonfigurovat pro zpracování těchto scénářů, která vám pomůže pochopit směrovací službu.  
  
## <a name="common-scenarios"></a>Obvyklé situace  
 Nejzákladnější použití směrovací služby je agregované několik cílových koncových bodů, aby se snížil počet koncových bodů vystavených klientským aplikacím, a pak pomocí filtrů zpráv směrují jednotlivé zprávy do správného cíle. Zprávy mohou být směrovány na základě logických nebo fyzických požadavků na zpracování, jako je například typ zprávy, který musí být zpracován konkrétní službou, nebo založený na libovolných obchodních potřebách, jako je například poskytování prioritních zpracování zpráv z konkrétního zdroje. V následující tabulce jsou uvedeny některé běžné scénáře a jejich zjištění:  
  
|Scénář|Kdy použít|  
|--------------|--------------|  
|Správa verzí služeb|Je potřeba, abyste podporovali víc verzí služby nebo v budoucnu mohli nasadit aktualizovanou službu.|  
|Vytváření oddílů dat služby|Je nutné rozdělit službu mezi několik hostitelů.|  
|Dynamická aktualizace|Pro zpracování změn nasazení služby je potřeba dynamicky znovu nakonfigurovat logiku směrování za běhu.|  
|Odesílání|Je nutné odeslat jednu zprávu do více koncových bodů.|  
|Přemostění protokolů|Přijímáte zprávy přes jeden transportní protokol a cílový koncový bod používá jiný protokol.|  
|Zpracování chyb|Je potřeba zajistit odolnost proti výpadkům sítě a selháním komunikace.|  
  
> [!NOTE]
> I když je mnoho z uvedených scénářů specifické pro konkrétní obchodní potřeby nebo požadavky na zpracování, plánování podpory dynamických aktualizací a využití zpracování chyb se často považuje za osvědčené postupy, protože umožňují upravit logiku směrování za běhu a obnovit z přechodné sítě a selhání komunikace.  
  
### <a name="service-versioning"></a>Verze služby  
 Když zavádíte novou verzi služby, musíte často zachovat předchozí verzi, dokud všichni klienti nepřešli do nové služby. To je obzvláště důležité, pokud je služba dlouhodobě spuštěným procesem, který vybírá dny, týdny nebo dokonce měsíce. Obvykle vyžaduje implementaci nové adresy koncového bodu pro novou službu při zachování původního koncového bodu pro předchozí verzi.  
  
 Pomocí směrovací služby můžete vystavit jeden koncový bod pro příjem zpráv z klientských aplikací a potom každou zprávu směrovat na správnou verzi služby na základě obsahu zprávy. Nejzákladnější implementace zahrnuje přidání vlastní hlavičky do zprávy, která označuje verzi služby, pomocí které se má zpráva zpracovat. Směrovací služba může použít XPathMessageFilter ke kontrole každé zprávy pro přítomnost vlastní hlavičky a ke směrování zprávy do příslušného cílového koncového bodu.  
  
 Postup pro vytvoření konfigurace správy verzí služby najdete v tématu [How to: Versioning Service](how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>Vytvoření oddílů dat služby  
 Při návrhu distribuovaného prostředí je často žádoucí rozprostřít zátěžové zatížení mezi více počítači, aby se zajistila vysoká dostupnost, aby se snížilo zatížení jednotlivých počítačů nebo aby poskytovalo vyhrazené prostředky pro určitou podmnožinu zpráv. I když směrovací služba nenahrazuje vyhrazené řešení vyrovnávání zatížení, je možné použít směrování na základě obsahu ke směrování jiných podobných zpráv do konkrétních míst. Například můžete mít požadavek na zpracování zpráv z konkrétního klienta odděleně od zpráv přijatých z jiných klientů.  
  
 Postup pro vytvoření konfigurace oddílů dat služby najdete v tématu [How to: Service data partitioning](how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Dynamické směrování  
 Často je žádoucí změnit konfiguraci směrování tak, aby vyhovovala měnícím se potřebám podniku, jako je například přidání trasy k novější verzi služby, změna kritérií směrování nebo změna cílového koncového bodu na konkrétní zprávu, na kterou filtr odkazuje. Směrovací služba vám umožní provést to prostřednictvím <xref:System.ServiceModel.Routing.RoutingExtension> , což vám umožní během běhu poskytnout nové konfigurace RoutingConfiguration. Nová konfigurace se projeví okamžitě, ale má vliv jenom na nové relace zpracovávané směrovací službou.  
  
 Postup pro implementaci dynamického směrování najdete v tématu [Postupy: Dynamická aktualizace](how-to-dynamic-update.md).
  
### <a name="multicast"></a>Odesílání  
 Při směrování zpráv obvykle směrujete jednotlivé zprávy do jednoho konkrétního cílového koncového bodu.  Občas ale budete muset směrovat kopii zprávy na více cílových koncových bodů. Chcete-li provést směrování vícesměrového vysílání, musí být splněny následující podmínky:  
  
- Obrazec kanálu nesmí být požadavkem na odpověď (i když může být jednosměrný nebo duplexní), protože klientská aplikace může v reakci na požadavek přijmout jenom jednu odpověď.  
  
- Při vyhodnocování zprávy musí být vráceno více filtrů na **hodnotu true** .  
  
 Pokud jsou tyto podmínky splněny, obdrží každý cílový koncový bod přidružený k filtru, který vrací hodnotu true, kopii zprávy.  
  
### <a name="protocol-bridging"></a>Přemostění protokolů  
 Při směrování zpráv mezi odlišnými protokoly SOAP služba Směrování používá rozhraní API WCF k převedení zprávy z jednoho protokolu na druhý. K tomu dochází automaticky v případě, že koncový bod služby vystavený směrovací službou používá jiný protokol než koncový bod klienta, na který jsou zprávy směrovány. Toto chování je možné zakázat, pokud používané protokoly nejsou standardní. je však nutné zadat vlastní kód přemostění.
  
### <a name="error-handling"></a>Zpracování chyb  
 V distribuovaném prostředí není běžné, že dojde k přechodným chybám sítě nebo komunikace. Bez zprostředkující služby, jako je směrovací služba, by režie zpracování takových selhání mohla spadat do klientské aplikace. Pokud klientská aplikace nezahrnuje konkrétní logiku pro opakování v případě chyby sítě nebo selhání komunikace a znalostí alternativních umístění, může se stát, že se uživateli před tím, než bude úspěšně zpracována cílová služba, zobrazí situace, kdy se zpráva musí odeslat několikrát. To může vést k nespokojenosti zákazníků s aplikací, jak je možné ho vnímat jako nespolehlivější.  
  
 Směrovací služba se pokusí tento scénář napravit tím, že poskytuje robustní funkce zpracování chyb pro zprávy, které nastanou při selhání souvisejícím se sítí nebo komunikací. Vytvořením seznamu možných cílových koncových bodů a přidružením tohoto seznamu ke každému filtru zpráv odeberete jediný bod selhání, který by měl mít jenom jeden možný cíl. V případě selhání se směrovací služba pokusí doručit zprávu do dalšího koncového bodu v seznamu, dokud se nevydá zpráva, dojde k selhání nekomunikace nebo byly vyčerpány všechny koncové body.  
  
 Postup pro konfiguraci zpracování chyb naleznete v tématu [How to: Erroring](how-to-error-handling.md).
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Správa verzí služby](how-to-service-versioning.md)  
  
 [Postupy: Vytvoření oddílů dat služby](how-to-service-data-partitioning.md)  
  
 [Postupy: Dynamická aktualizace](how-to-dynamic-update.md)  
  
 [Postupy: Zpracování chyb](how-to-error-handling.md)  
  
## <a name="see-also"></a>Viz také

- [Směrování – úvod](routing-introduction.md)
