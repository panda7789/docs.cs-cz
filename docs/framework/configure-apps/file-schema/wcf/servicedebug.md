---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 1ab7058d8667344197e8bc1ddc59cc7200f22270
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268558"
---
# <a name="servicedebug"></a>\<serviceDebug>
Určuje funkce informace nápovědy a ladění pro službu Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceDebug>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|httpHelpPageBinding|Hodnotu řetězce, který určuje typ vazby, jenž se dá použít při HTTP se používá pro přístup ke stránce nápovědy služby.<br /><br /> Pouze vazby s vnitřní elementy vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Řetězec určující název vazby určený v `httpHelpPageBinding` atribut, který odkazuje Další informace o konfiguraci této vazby. Se stejným názvem musí být definován v `<bindings>` oddílu.|  
|httpHelpPageEnabled|Logická hodnota, které řídí, zda publikuje služba WCF stránku HTML nápovědy na adrese určené `httpHelpPageUrl` atribut. Výchozí hodnota je `true`.<br /><br /> Tuto vlastnost lze nastavit `false` zakázat publikování stránku nápovědy HTML viditelné pro prohlížeče HTML.<br /><br /> K zajištění nápovědy HTML stránka publikována do umístění, řídí `httpHelpPageUrl` atributu, musí tento atribut nastavíte `true`. Kromě toho splněna jedna z následujících podmínek musí také být:<br /><br /> – `httpHelpPageUrl` Atribut je absolutní adresu, která podporuje schéma protokolu HTTP.<br />-Je základní adresa pro službu, která podporuje schéma protokolu HTTP.<br /><br /> I když je vyvolána výjimka, pokud je přiřazena absolutní adresu, která nepodporuje schéma protokolu HTTP `httpHelpPageUrl` atribut, všechny další scénáře, ve které ani jeden z předchozích kritéria je splněny má za následek žádná výjimka a žádná stránka nápovědy HTML.|  
|httpHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní založené na protokolu HTTP adresu URL vlastního HTML nápovědy, soubor uživatel vidí při prohlížení koncového bodu pomocí prohlížeče HTML.<br /><br /> Tento atribut slouží k povolení použití vlastního souboru nápovědy jazyka HTML, který je vrácený z požadavku HTTP/Get, například z prohlížeče HTML. Umístění souboru nápovědy jazyka HTML je vyřešen následujícím způsobem.<br /><br /> 1.  Pokud hodnota tohoto atributu je relativní adresa, umístění souboru nápovědy jazyka HTML je hodnota základní adresa služby, který podporuje požadavky HTTP, a navíc tuto hodnotu vlastnosti.<br />2.  Pokud hodnota tohoto atributu je absolutní adresu a podporuje požadavky HTTP, umístění souboru nápovědy jazyka HTML je hodnota této vlastnosti.<br />3.  Pokud je hodnota tohoto atributu je absolutní ale nepodporuje požadavků HTTP, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze tehdy, když `httpHelpPageEnabled` atribut je `true`.|  
|httpsHelpPageBinding|Hodnotu řetězce, který určuje typ vazby, jenž se dá použít při HTTPS se používá pro přístup ke stránce nápovědy služby.<br /><br /> Pouze vazby s vnitřní elementy vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Řetězec určující název vazby určený v `httpsHelpPageBinding` atribut, který odkazuje Další informace o konfiguraci této vazby. Se stejným názvem musí být definován v `<bindings>` oddílu.|  
|httpsHelpPageEnabled|Logická hodnota, které řídí, zda publikuje služba WCF stránku HTML nápovědy na adrese určené `httpsHelpPageUrl` atribut. Výchozí hodnota je `true`.<br /><br /> Tuto vlastnost lze nastavit `false` zakázat publikování stránku nápovědy HTML viditelné pro prohlížeče HTML.<br /><br /> K zajištění nápovědy HTML stránka publikována do umístění, řídí `httpsHelpPageUrl` atributu, musí tento atribut nastavíte `true`. Kromě toho splněna jedna z následujících podmínek musí také být:<br /><br /> – `httpsHelpPageUrl` Atribut je absolutní adresu, která podporuje protokol schéma HTTPS.<br />-Je základní adresa služby, který podporuje protokol schéma HTTPS.<br /><br /> I když je vyvolána výjimka, pokud je přiřazena absolutní adresu, která nepodporuje schéma protokolu HTTPS `httpsHelpPageUrl` atribut, všechny další scénáře, ve které ani jeden z předchozích kritéria je splněny má za následek žádná výjimka a žádná stránka nápovědy HTML.|  
|httpsHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní založený na protokolu HTTPS adresu URL vlastního HTML nápovědy, soubor uživatel vidí při prohlížení koncového bodu pomocí prohlížeče HTML.<br /><br /> Tento atribut slouží k povolení použití vlastního souboru nápovědy jazyka HTML, který je vrácený z požadavku HTTPS/Get, například z prohlížeče HTML. Umístění souboru nápovědy jazyka HTML je vyřešen následujícím způsobem:<br /><br /> – Pokud je hodnota této vlastnosti je relativní adresa, umístění souboru nápovědy jazyka HTML, je hodnota základní adresa služby, který podporuje požadavky HTTPS, a navíc tuto hodnotu vlastnosti.<br />– Pokud je hodnota této vlastnosti je absolutní adresu a podporuje požadavky HTTPS, je umístění souboru nápovědy jazyka HTML hodnota této vlastnosti.<br />– Pokud je hodnota této vlastnosti je absolutní, ale nepodporuje požadavky HTTPS, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze tehdy, když `httpHelpPageEnabled` atribut je `true`.|  
|Třídu IncludeExceptionDetailInFaults|Hodnota, která určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění. Výchozí hodnota je `false`.<br /><br /> Pokud tento atribut nastavíte na `true`, můžete povolit tok informací o řízené výjimce do klienta pro účely ladění a publikování informací soubory HTML pro procházení služby do webových prohlížečů uživatelů. **Upozornění:**  Vracející informace o spravované výjimce klientům může představovat bezpečnostní riziko. Je to proto, že podrobnosti o výjimce zveřejnit informace o implementaci vnitřní chybě služby, které by mohly používat neoprávněným klientů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení `includeExceptionDetailInFaults` k `true` umožňuje vrátit jakoukoliv výjimku, která je vyvolána kódem aplikace, i v případě, že výjimka není deklarován pomocí služby <xref:System.ServiceModel.FaultContractAttribute>. Toto nastavení je užitečné při ladění v případech, kde je serveru vyvolání neočekávané výjimky. Pomocí tohoto atributu je vrácena serializovanou formu neznámá výjimka a můžete prozkoumat další podrobnosti o výjimce.  
  
> [!CAUTION]
>  Vracející informace o spravované výjimce klientů může být bezpečnostní riziko, protože podrobnosti o výjimce zveřejnit informace o implementaci vnitřní chybě služby, které by mohly používat neoprávněným klientů. Z důvodu zabezpečení problematiku důrazně doporučujeme, můžete tak učinit pouze v řízené scénáře ladění. Měli byste nastavit `includeExceptionDetailInFaults` k `false` při nasazování aplikace.  
  
 Podrobnosti o řešení problémů zabezpečení související s spravované výjimky najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Ukázku kódu naleznete v tématu [chování ladění služby](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Můžete také nastavit `httpsHelpPageEnabled` a `httpsHelpPageUrl` k povolení nebo zakázání stránky s nápovědou. Každá služba Volitelně můžete zveřejnit stránce nápovědy, který obsahuje informace o službě včetně koncový bod pro získání WSDL pro službu. To se dá nastavit tak, že nastavíte `httpHelpPageEnabled` k `true`. To umožňuje na stránce nápovědy, který se má vrátit požadavek GET na základní adresu služby. Tuto adresu můžete změnit nastavením `httpHelpPageUrl` atribut. Kromě toho lze zvýšit tím zabezpečení pomocí protokolu HTTPS místo protokolu HTTP.  
  
 Volitelný `httpHelpPageBinding` a `httpHelpPageBinding` atributy umožňují konfigurovat vazby používá pro přístup k webové stránce služby. Pokud zadané není, výchozí vazby (`HttpTransportBindingElement`, v případě protokolu HTTP a `HttpsTransportBindingElement`, v případě protokolu HTTPS) se používají pro přístup k stránce nápovědy služby podle potřeby. Všimněte si, že tyto atributy nelze použít s integrovanou vazeb WCF. Pouze vazby s vnitřní elementy vazby, které podporují xref:System.ServiceModel.Channels.IReplyChannel > bude podporovat. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Zpracování výjimek a chyb](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Chování při ladění služby](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
