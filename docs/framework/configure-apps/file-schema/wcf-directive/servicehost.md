---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "76787804"
---
# <a name="servicehost"></a>\@Hostiteli

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

### <a name="service"></a>Služba

Název typu CLR hostované služby. Mělo by se jednat o kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.

### <a name="factory"></a>Objekt pro vytváření

Název typu CLR objektu pro vytváření hostitele služby, který se používá k vytvoření instance hostitele služby. Tento atribut je nepovinný. Je-li tento parametr zadán, <xref:System.ServiceModel.Activation.ServiceHostFactory> je použita výchozí hodnota, která vrací instanci <xref:System.ServiceModel.ServiceHost> .

### <a name="debug"></a>Ladění

Určuje, zda má být služba Windows Communication Foundation (WCF) zkompilována se symboly ladění. `true`Pokud má být služba WCF zkompilována se symboly ladění; v opačném případě `false` .

### <a name="language"></a>Jazyk

Určuje jazyk použitý při kompilaci veškerého vloženého kódu v rámci souboru (. svc). Hodnoty mohou představovat libovolný. NET – podporovaný jazyk, včetně `C#` , `VB` a `JS` , který odkazuje na C#, Visual Basic a JScript .NET, v uvedeném pořadí. Tento atribut je nepovinný.

### <a name="codebehind"></a>CodeBehind

Určuje zdrojový soubor, který implementuje webovou službu XML, pokud třída, která implementuje webovou službu XML, není umístěna ve stejném souboru a nebyla zkompilována do sestavení a umístěna do adresáře *\Bin* .

## <a name="remarks"></a>Poznámky

<xref:System.ServiceModel.ServiceHost>Použití pro hostování služby je bod rozšíření v rámci programovacího modelu Windows Communication Foundation (WCF). Model továrny se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> , protože je, potenciálně polymorfního typu, který by hostitelský prostředí nemělo vytvářet přímo.

Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost> . Můžete ale zadat vlastní továrnu (jednu, která vrací vašeho odvozeného hostitele) zadáním názvu typu CLR implementace výroby v `@ServiceHost` direktivě.

Pokud chcete použít vlastní objekt pro vytváření hostitele služby místo výchozí továrny, stačí zadat název typu v `@ServiceHost` direktivě následujícím způsobem.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

Udržujte implementace továrny co nejblíže. Pokud máte spoustu vlastní logiky, váš kód je více použitelný, pokud tuto logiku vložíte do svého hostitele místo do objektu factory.

Chcete-li například povolit koncový bod s povoleným AJAX pro `MyService` , zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu `Factory` atributu místo výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> v `@ServiceHost` direktivě, jak je znázorněno v následujícím příkladu:

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>Viz také

- [Vlastní hostitel služby](../../../wcf/samples/custom-service-host.md)
