---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 4eb79cc91ef489501c4c8bb6311f240d855ed053
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399643"
---
# \<serviceDebug>
Určuje funkce ladění a informací o nápovědě pro službu Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDebug>**  
  
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
|httpHelpPageBinding|Řetězcová hodnota, která určuje typ vazby, která se má použít, když se k přístupu na stránku služby s podporou protokolu HTTP využívá protokol HTTP.<br /><br /> Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> . Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .|  
|httpHelpPageBindingConfiguration|Řetězec, který určuje název vazby, která je zadána v `httpHelpPageBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby. V části se musí definovat stejný název `<bindings>` .|  
|httpHelpPageEnabled|Logická hodnota, která určuje, zda na adrese určené atributem publikuje služba WCF stránku HTML s HTML `httpHelpPageUrl` . Výchozí formát je `true`.<br /><br /> Tuto vlastnost lze nastavit na hodnotu `false` , chcete-li zakázat publikování stránky s nápovědě HTML, která je viditelná pro prohlížeče HTML.<br /><br /> Chcete-li zajistit, aby byla stránka s HTML Help publikována v umístění kontrolovaném `httpHelpPageUrl` atributem, je nutné nastavit tento atribut na `true` . Kromě toho musí být splněna jedna z následujících podmínek:<br /><br /> – `httpHelpPageUrl` Atribut je absolutní adresa, která podporuje schéma protokolu HTTP.<br />– Pro službu je k dispozici základní adresa, která podporuje schéma protokolu HTTP.<br /><br /> I když je vyvolána výjimka, pokud absolutní adresa, která nepodporuje schéma protokolu HTTP, je přiřazena k `httpHelpPageUrl` atributu, jakýmkoli jiným scénářem, ve kterém není splněno žádné předchozí kritérium, nevrátí žádnou výjimku ani stránku HTML Help.|  
|httpHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní adresu URL založenou na protokolu HTTP vlastního souboru HTML Help, se uživateli zobrazí při prohlížení koncového bodu pomocí prohlížeče HTML.<br /><br /> Tento atribut lze použít k povolení použití vlastního souboru HTML Help, který je vrácen z požadavku HTTP/GET, například z prohlížeče HTML. Umístění souboru HTML Help je vyřešeno následujícím způsobem.<br /><br /> 1. Pokud je hodnota tohoto atributu relativní adresou, umístění souboru HTML Help je hodnota základní adresy služby, která podporuje požadavky HTTP, a také hodnotu této vlastnosti.<br />2. Pokud je hodnota tohoto atributu absolutní adresou a podporuje požadavky HTTP, umístění souboru HTML Help je hodnota této vlastnosti.<br />3. Pokud je hodnota tohoto atributu absolutní, ale nepodporuje požadavky HTTP, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze v případě, že `httpHelpPageEnabled` je atribut `true` .|  
|httpsHelpPageBinding|Řetězcová hodnota, která určuje typ vazby, která se má použít, když se k přístupu na stránku služby Service Help používá protokol HTTPS.<br /><br /> Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují <xref:System.ServiceModel.Channels.IReplyChannel> . Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .|  
|httpsHelpPageBindingConfiguration|Řetězec, který určuje název vazby, která je zadána v `httpsHelpPageBinding` atributu, který odkazuje na Další informace o konfiguraci této vazby. V části se musí definovat stejný název `<bindings>` .|  
|httpsHelpPageEnabled|Logická hodnota, která určuje, zda na adrese určené atributem publikuje služba WCF stránku HTML s HTML `httpsHelpPageUrl` . Výchozí formát je `true`.<br /><br /> Tuto vlastnost lze nastavit na hodnotu `false` , chcete-li zakázat publikování stránky s nápovědě HTML, která je viditelná pro prohlížeče HTML.<br /><br /> Chcete-li zajistit, aby byla stránka s HTML Help publikována v umístění kontrolovaném `httpsHelpPageUrl` atributem, je nutné nastavit tento atribut na `true` . Kromě toho musí být splněna jedna z následujících podmínek:<br /><br /> – `httpsHelpPageUrl` Atribut je absolutní adresa, která podporuje schéma protokolu HTTPS.<br />– Pro službu je k dispozici základní adresa, která podporuje schéma protokolu HTTPS.<br /><br /> I když je vyvolána výjimka, pokud absolutní adresa, která nepodporuje schéma protokolu HTTPS, je přiřazena k `httpsHelpPageUrl` atributu, jakýmkoli jiným scénářem, ve kterém není splněno žádné předchozí kritérium, nevrátí žádnou výjimku ani stránku HTML Help.|  
|httpsHelpPageUrl|Identifikátor URI, který určuje relativní nebo absolutní adresu URL založenou na protokolu HTTPS vlastního souboru HTML Help, se uživateli zobrazí při prohlížení koncového bodu pomocí prohlížeče HTML.<br /><br /> Tento atribut lze použít k povolení použití vlastního souboru HTML Help, který je vrácen z požadavku HTTPS/Get, například z prohlížeče HTML. Umístění souboru HTML Help je vyřešeno následujícím způsobem:<br /><br /> – Pokud je hodnota této vlastnosti relativní adresa, umístění souboru HTML Help je hodnota základní adresy služby, která podporuje požadavky HTTPS, a tuto hodnotu vlastnosti.<br />– Pokud je hodnota této vlastnosti absolutní adresou a podporuje požadavky HTTPS, umístění souboru HTML Help je hodnota této vlastnosti.<br />– Pokud je hodnota této vlastnosti absolutní, ale nepodporuje požadavky HTTPS, je vyvolána výjimka.<br /><br /> Tento atribut je platný pouze v případě, že `httpHelpPageEnabled` je atribut `true` .|  
|Zapnete IncludeExceptionDetailInFaults|Hodnota, která určuje, zda se mají zahrnout informace o spravované výjimce v podrobnostech o chybách protokolu SOAP vracené klientovi pro účely ladění. Výchozí formát je `false`.<br /><br /> Pokud tento atribut nastavíte na `true` , můžete povolit tok informací o spravovaných výjimkách klientovi pro účely ladění a také publikování souborů s informacemi HTML pro uživatele, kteří procházejí službu ve webových prohlížečích. **Upozornění:**  Vrácení informací o spravované výjimce klientům může představovat bezpečnostní riziko. Důvodem je skutečnost, že podrobnosti o výjimce zpřístupňují informace o implementaci interní služby, které by mohly být používány neautorizovanými klienty.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení `includeExceptionDetailInFaults` `true` povolují službě vracet jakékoli výjimky, které jsou vyvolány kódem aplikace, i v případě, že výjimka není deklarována pomocí <xref:System.ServiceModel.FaultContractAttribute> . Toto nastavení je užitečné při ladění případů, kdy server vyvolává neočekávanou výjimku. Pomocí tohoto atributu je vrácena serializovaná forma neznámé výjimky a můžete prostudovat další podrobnosti o výjimce.  
  
> [!CAUTION]
> Vrácení spravovaných informací o výjimce klientům může představovat bezpečnostní riziko, protože podrobnosti o výjimce zpřístupňují informace o interní implementaci služby, kterou by mohli používat neoprávnění klienti. Z důvodu problémů se zabezpečením se důrazně doporučuje pouze v rámci řízených scénářů ladění. Při `includeExceptionDetailInFaults` nasazování aplikace byste měli nastavit na `false` .  
  
 Podrobnosti o problémech zabezpečení souvisejících se spravovanými výjimkami najdete v tématu [určení a manipulace s chybami ve smlouvách a službách](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md). Ukázku kódu naleznete v tématu [chování ladění služby](../../../wcf/samples/service-debug-behavior.md).  
  
 Můžete také nastavit `httpsHelpPageEnabled` a `httpsHelpPageUrl` Povolit nebo zakázat stránku s usnadněním. Každá služba může volitelně vystavit stránku s nápovědu obsahující informace o službě, včetně koncového bodu pro získání WSDL pro službu. To lze povolit nastavením `httpHelpPageEnabled` na `true` . Tím umožníte, aby se stránka s Nápověda vrátila do žádosti o získání základní adresy služby. Tuto adresu můžete změnit nastavením `httpHelpPageUrl` atributu. Kromě toho můžete nastavit toto zabezpečení pomocí protokolu HTTPS místo HTTP.  
  
 Volitelné `httpHelpPageBinding` atributy a `httpHelpPageBinding` umožňují konfigurovat vazby používané pro přístup k webové stránce služby. Pokud nejsou zadány, použijí se výchozí vazby ( `HttpTransportBindingElement` v případě protokolu HTTP a `HttpsTransportBindingElement` v případě protokolu HTTPS) pro přístup stránky s podporou služby podle potřeby. Všimněte si, že nemůžete použít tyto atributy s předdefinovanými vazbami WCF. Budou podporovány pouze vazby s vnitřními prvky vazby, které podporují odkazy XREF: System. ServiceModel. Channels. IReplyChannel>. Kromě toho <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musí být vlastnost vazby <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Určování a zpracování chyb v kontraktech a službách](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Zpracování výjimek a chyb](../../../wcf/extending/handling-exceptions-and-faults.md)
- [Chování ladění služby](../../../wcf/samples/service-debug-behavior.md)
