---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: dd3dd026749ccc299cd922b79dcae8ccbcc722d8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968831"
---
# <a name="servicehost"></a>\@ServiceHost
Přidruží továrnu, která se používá k vytváření hostitele služby pro hostování služby, a dalších aspektů programování potřebných pro přístup k nebo zkompilování hostujícího kódu, který je k dispozici v souboru. svc.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a>Atributy  
  
#### <a name="service"></a>Služba  
 Název typu CLR hostované služby. Mělo by se jednat o kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.  
  
#### <a name="factory"></a>instalací  
 Název typu CLR objektu pro vytváření hostitele služby, který se používá k vytvoření instance hostitele služby. Tento atribut je nepovinný. Je-li tento parametr zadán, je použita výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory>, která vrací instanci <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Ladit  
 Určuje, zda má být služba Windows Communication Foundation (WCF) zkompilována se symboly ladění. `true`, zda má být služba WCF kompilována se symboly ladění; v opačném případě `false`.  
  
#### <a name="language"></a>Jazyk  
 Určuje jazyk použitý při kompilaci veškerého vloženého kódu v rámci souboru (. svc). Hodnoty mohou představovat libovolný. Podporovaný jazyk, včetně C#jazyků, VB a js, které odkazují na C#, Visual Basic .NET a JScript .NET, v uvedeném pořadí. Tento atribut je nepovinný.  
  
#### <a name="codebehind"></a>CodeBehind  
 Určuje zdrojový soubor, který implementuje webovou službu XML, pokud třída, která implementuje webovou službu XML, není umístěna ve stejném souboru a nebyla zkompilována do sestavení a umístěna do adresáře \Bin.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.ServiceModel.ServiceHost>, která se používá k hostování služby, je bod rozšíření v programovacím modelu Windows Communication Foundation (WCF). Model továrny slouží k vytvoření instance <xref:System.ServiceModel.ServiceHost>, protože je potenciálně polymorfní polymorfní typ, který by hostitelské prostředí nemělo vytvářet přímo.  
  
 Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost>. Můžete ale zadat vlastní továrnu (jednu, která vrací vašeho odvozeného hostitele) zadáním názvu typu CLR implementace továrny v direktivě [ServiceHost\@](servicehost.md) .  
  
 Pokud chcete použít vlastní objekt pro vytváření hostitele služby místo výchozí továrny, stačí zadat název typu v direktivě [@ServiceHost](servicehost.md) následujícím způsobem:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Udržujte implementace továrny co nejblíže. Pokud máte spoustu vlastní logiky, váš kód je více použitelný, pokud tuto logiku vložíte do svého hostitele místo do objektu factory.  
  
 Chcete-li například povolit koncový bod s povoleným AJAX pro `MyService`, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hodnoty atributu `Factory` namísto výchozího <xref:System.ServiceModel.Activation.ServiceHostFactory>v direktivě [@ServiceHost](servicehost.md) , jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vlastní hostitel služby](../../../wcf/samples/custom-service-host.md)
