---
title: '&lt;serviceDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cdd5d8a05354ad6f0df8343d546fd6cd1e8eac4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicedebuggt"></a>&lt;serviceDebug&gt;
Určuje funkce informace o ladění a nápovědu pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceDebug >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceDebug     httpHelpPageBinding="String"    httpHelpPageBindingConfiguration="String"  
    httpHelpPageEnabled="Boolean"  
    httpHelpPageUrl="Uri"  
    httpsHelpPageBinding="String"    httpsHelpPageBindingConfiguration="String"  
    httpsHelpPageEnabled="Boolean"  
    httpsHelpPageUrl="Uri"  
    includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|httpHelpPageBinding|Hodnotu řetězce, který určuje typ vazby má být použit při HTTP je využívat pro přístup na stránku nápovědy služby.<br /><br /> Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Řetězec, který určuje název vazby, který je uveden v `httpHelpPageBinding` atribut, který odkazuje na další konfigurační informace této vazby. Se stejným názvem, musí být definován v `<bindings>` oddílu.|  
|httpHelpPageEnabled|Logická hodnota. hodnota této řídí, zda [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] publikuje stránku nápovědy HTML na adrese určeného `httpHelpPageUrl` atribut. Výchozí hodnota je `true`.<br /><br /> Tuto vlastnost lze nastavit `false` zakázat publikování stránku nápovědy HTML do prohlížečů HTML viditelné.<br /><br /> K zajištění nápovědy HTML stránka publikována do umístění, které řídí `httpHelpPageUrl` atributu, je nutné tento atribut nastavit na `true`. Kromě toho splněna jedna z následujících podmínek musí také být:<br /><br /> -Na `httpHelpPageUrl` atribut je absolutní adresu, která podporuje schéma protokolu HTTP.<br />– Je základní adresa pro službu, která podporuje schéma protokolu HTTP.<br /><br /> I když je vyvolána výjimka, pokud absolutní adresu, která nepodporuje schéma protokolu HTTP je přiřazen k `httpHelpPageUrl` atribut, všechny další scénáře, ve které žádný z předchozí kritéria je nesplnění má za následek žádná výjimka a žádná stránka nápovědy HTML.|  
|httpHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní založené na protokolu HTTP adresu URL vlastní HTML pomoci souboru uživatel vidí při koncový bod je zobrazit pomocí prohlížeče HTML.<br /><br /> Tento atribut můžete povolit použití vlastní soubor nápovědy HTML vrácená z žádosti HTTP/Get, například prohlížeči HTML. Umístění soubor nápovědy HTML vyřešen následujícím způsobem.<br /><br /> 1.  Pokud hodnota tohoto atributu je relativní adresa, umístění soubor nápovědy HTML je hodnota základní adresa služby, který podporuje požadavky HTTP, plus tuto hodnotu vlastnosti.<br />2.  Pokud hodnota tohoto atributu je absolutní adresu a podporuje požadavky HTTP, umístění soubor nápovědy HTML je hodnota této vlastnosti.<br />3.  Pokud hodnota tohoto atributu je absolutní, ale nepodporuje požadavků HTTP, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze tehdy, když `httpHelpPageEnabled` atribut je `true`.|  
|httpsHelpPageBinding|Hodnotu řetězce, který určuje typ vazby má být použit při přístupu na stránku nápovědy služby je využívat protokol HTTPS.<br /><br /> Jenom vazby s prvky vnitřní vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Řetězec, který určuje název vazby, který je uveden v `httpsHelpPageBinding` atribut, který odkazuje na další konfigurační informace této vazby. Se stejným názvem, musí být definován v `<bindings>` oddílu.|  
|httpsHelpPageEnabled|Logická hodnota. hodnota této řídí, zda [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] publikuje stránku nápovědy HTML na adrese určeného `httpsHelpPageUrl` atribut. Výchozí hodnota je `true`.<br /><br /> Tuto vlastnost lze nastavit `false` zakázat publikování stránku nápovědy HTML do prohlížečů HTML viditelné.<br /><br /> K zajištění nápovědy HTML stránka publikována do umístění, které řídí `httpsHelpPageUrl` atributu, je nutné tento atribut nastavit na `true`. Kromě toho splněna jedna z následujících podmínek musí také být:<br /><br /> -Na `httpsHelpPageUrl` atribut je absolutní adresu, která podporuje protokol schéma HTTPS.<br />– Je základní adresa služby, který podporuje protokol schéma HTTPS.<br /><br /> I když je vyvolána výjimka, pokud absolutní adresu, která nepodporuje protokol schéma HTTPS je přiřazen k `httpsHelpPageUrl` atribut, všechny další scénáře, ve které žádný z předchozí kritéria je nesplnění má za následek žádná výjimka a žádná stránka nápovědy HTML.|  
|httpsHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní založený na protokolu HTTPS adresu URL vlastní HTML pomoci souboru uživatel vidí při koncový bod je zobrazit pomocí prohlížeče HTML.<br /><br /> Tento atribut můžete povolit použití vlastní soubor nápovědy HTML vrácená z požadavek HTTPS nebo získat například prohlížeči HTML. Umístění soubor nápovědy HTML je přeložit takto:<br /><br /> – Pokud je hodnota této vlastnosti je relativní adresa, umístění soubor nápovědy HTML je hodnota základní adresa služby, který podporuje požadavky HTTPS, plus tuto hodnotu vlastnosti.<br />– Pokud je hodnota této vlastnosti je absolutní adresu a podporuje požadavky HTTPS, je umístění soubor nápovědy HTML hodnota této vlastnosti.<br />– Pokud je hodnota této vlastnosti absolutní ale nepodporuje požadavky HTTPS, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze tehdy, když `httpHelpPageEnabled` atribut je `true`.|  
|Třídu IncludeExceptionDetailInFaults|Hodnota, která určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácen do klienta pro účely ladění. Výchozí hodnota je `false`.<br /><br /> Pokud tento atribut nastavíte na `true`, můžete povolit tok spravovaných výjimek informací na klienta pro účely ladění a také publikace soubory HTML informace pro uživatele procházení služby do webových prohlížečů. **Upozornění:** vrácení informací o spravovaných výjimce klientům může být bezpečnostní riziko. To je proto podrobnosti o výjimce zveřejnění informace o interní služby implementace, která může neoprávněným klienty.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení `includeExceptionDetailInFaults` k `true` umožňuje službě vrátit jakékoli výjimky vyvolané kódem aplikace i v případě, že výjimka není deklarovaný pomocí <xref:System.ServiceModel.FaultContractAttribute>. Toto nastavení je užitečné při ladění případech, kde je serveru došlo k neočekávané výjimce. Pomocí tohoto atributu se vrátí serializovaný formu neznámé výjimce a můžete zkontrolovat podrobnosti výjimky.  
  
> [!CAUTION]
>  Vracejících informace o spravovaných výjimce klientům může být bezpečnostní riziko, protože informace o interní služby implementace, která může neoprávněným klienty vystavit podrobnosti o výjimce. Z důvodu zabezpečení problémy související se situací důrazně doporučujeme vám jenom to v řízené scénáře ladění. Měli byste nastavit `includeExceptionDetailInFaults` k `false` při nasazení aplikace.  
  
 Podrobnosti o problémech zabezpečení související s spravovaných výjimek najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Ukázka kódu, najdete v části [chování ladění služby](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Můžete také nastavit `httpsHelpPageEnabled` a `httpsHelpPageUrl` chcete povolit nebo zakázat tuto stránku nápovědy. Každé služby můžete volitelně vystavit stránku nápovědy, která obsahuje informace o službě včetně koncový bod získat WSDL pro službu. To se dá nastavit nastavením `httpHelpPageEnabled` k `true`. To umožňuje stránku nápovědy a vrátit požadavek GET na adresu základní služby. Tuto adresu můžete změnit nastavením `httpHelpPageUrl` atribut. Kromě toho můžete nastavit to zabezpečené pomocí protokolu HTTPS místo protokolu HTTP.  
  
 Volitelné `httpHelpPageBinding` a `httpHelpPageBinding` atributů umožňují konfigurovat vazby používá pro přístup k webové stránce služby. Pokud nejsou zadané, výchozí vazby (`HttpTransportBindingElement`, v případě protokolu HTTP a `HttpsTransportBindingElement`, v případě HTTPS) se používá pro přístup k stránka nápovědy služby podle potřeby. Všimněte si, že tyto atributy nelze použít s integrovanou vazby WCF. Jenom vazby s prvky vnitřní vazby, které podporují xref:System.ServiceModel.Channels.IReplyChannel > budou podporovány. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceDebugElement>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Zpracování výjimek a chyb](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Chování při ladění služby](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
