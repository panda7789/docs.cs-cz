---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920340"
---
# <a name="servicehost"></a>\@Hostiteli
Přidruží továrnu, která se používá k vytváření hostitele služby pro hostování služby, a dalších aspektů programování potřebných pro přístup k nebo zkompilování hostujícího kódu, který je k dispozici v souboru. svc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Atributy  
  
#### <a name="service"></a>Služba  
 Název typu CLR hostované služby. Mělo by se jednat o kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.  
  
#### <a name="factory"></a>Instalací  
 Název typu CLR objektu pro vytváření hostitele služby, který se používá k vytvoření instance hostitele služby. Tento atribut je nepovinný. Je-li tento parametr zadán <xref:System.ServiceModel.Activation.ServiceHostFactory> , je použita výchozí hodnota, která vrací <xref:System.ServiceModel.ServiceHost>instanci.  
  
#### <a name="debug"></a>Ladění  
 Určuje, zda má být služba Windows Communication Foundation (WCF) zkompilována se symboly ladění. `true`Pokud má být služba WCF zkompilována se symboly ladění; v opačném případě. `false`  
  
#### <a name="language"></a>Jazyk  
 Určuje jazyk použitý při kompilaci veškerého vloženého kódu v rámci souboru (. svc). Hodnoty mohou představovat libovolný. Podporovaný jazyk, včetně C#jazyků, VB a js, které odkazují na C#, Visual Basic .NET a JScript .NET, v uvedeném pořadí. Tento atribut je nepovinný.  
  
#### <a name="codebehind"></a>CodeBehind  
 Určuje zdrojový soubor, který implementuje webovou službu XML, pokud třída, která implementuje webovou službu XML, není umístěna ve stejném souboru a nebyla zkompilována do sestavení a umístěna do adresáře \Bin.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.ServiceModel.ServiceHost> Použití pro hostování služby je bod rozšíření v rámci programovacího modelu Windows Communication Foundation (WCF). Model továrny se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> , protože je, potenciálně polymorfního typu, který by hostitelský prostředí nemělo vytvářet přímo.  
  
 Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření <xref:System.ServiceModel.ServiceHost>instance. Můžete ale zadat vlastní továrnu (jednu, která vrací vašeho odvozeného hostitele) zadáním názvu typu CLR implementace továrny v [ \@](servicehost.md) direktivě ServiceHost.  
  
 Pokud chcete použít vlastní objekt pro vytváření hostitele služby místo výchozího objektu pro vytváření, stačí zadat název typu v [@ServiceHost](servicehost.md) direktivě následujícím způsobem:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Udržujte implementace továrny co nejblíže. Pokud máte spoustu vlastní logiky, váš kód je více použitelný, pokud tuto logiku vložíte do svého hostitele místo do objektu factory.  
  
 Chcete-li například povolit koncový bod s povoleným AJAX `MyService`pro, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> zadejte `Factory` pro hodnotu atributu místo výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory>v [@ServiceHost](servicehost.md) direktivě, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Viz také:

- [Vlastní hostitel služby](../../../wcf/samples/custom-service-host.md)
