---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875678"
---
# <a name="servicehost"></a>\@Hostitel služby
Přidruží objekt pro vytváření použitý k vytvoření hostitele služby pomocí ní zajistit také jejich hostování a ostatní programovací aspekty vyžaduje přístup k nebo zkompilovat kód hostování zadaný v souboru SVC.  
  
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
 Název typu CLR hostované služby. To by měl být úplný název typu, který implementuje jednu nebo více kontakty ke službě.  
  
#### <a name="factory"></a>objekt pro vytváření  
 Název typu CLR objektu pro vytváření hostitele služby použít k vytvoření instance hostitele služby. Tento atribut je volitelný. Pokud tento parametr zadán, výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> se používá, která vrací instanci <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Ladit  
 Určuje, zda služby Windows Communication Foundation (WCF) by měl být kompilována se symboly ladění. `true` Pokud se služba WCF by měl být kompilována se symboly ladění; v opačném případě `false`.  
  
#### <a name="language"></a>Jazyk  
 Určuje jazyk použitý při kompilaci všech vložených kódu v souboru (.svc). Hodnoty mohou představovat všechny. NET – podporované jazyky, včetně C#, VB a JS, které se odkazují na C#, Visual Basic .NET a JScript .NET, v uvedeném pořadí. Tento atribut je volitelný.  
  
#### <a name="codebehind"></a>CodeBehind  
 Určuje zdrojový soubor, který implementuje webové služby XML, třídy, která implementuje webové služby XML není umístěný ve stejném souboru a nebyl po kompilovány do sestavení a umístěn v adresáři \Bin.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.ServiceModel.ServiceHost> Použít k hostování služby je bodu rozšiřitelnosti v rámci programovací model Windows Communication Foundation (WCF). Objekt pro vytváření vzorek se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> protože se jedná, případně polymorfní typ, který by neměl přímo vytvořit instanci hostitelského prostředí.  
  
 Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost>. Ale můžete zadat vlastní objekt pro vytváření (jedna, která vrací odvozené hostitelů) tak, že zadáte název typu CLR továrny implementace v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice.  
  
 Pokud chcete použít objekt pro vytváření hostitele služby vlastní vlastní místo výchozí objekt pro vytváření, stačí zadat název typu v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice následujícím způsobem:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Udržujte co nejlehčí factory implementace. Pokud máte velké množství vlastní logiku, váš kód je více opakovaně použitelné, pokud jste tuto logiku umístěte hostitele místo uvnitř objekt pro vytváření.  
  
 Například pro povolení koncového bodu s povoleným AJAX pro `MyService`, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu vlastnosti `Factory` atribut místo výchozího <xref:System.ServiceModel.Activation.ServiceHostFactory>v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv jako je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vlastní hostitel služby](../../../../../docs/framework/wcf/samples/custom-service-host.md)
