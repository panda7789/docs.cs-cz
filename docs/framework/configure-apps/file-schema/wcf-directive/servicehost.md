---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 5498c300ab126bbc4e08cd228e3e7b48e905932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servicehost"></a>@ServiceHost
Přidruží objekt pro vytváření použitý k vytvoření hostitele služby se službou pro hostování a ostatní programovací aspekty vyžaduje přístup k nebo zkompilovat kód hostování zadaný v souboru .svc.  
  
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
 Název typu CLR hostované služby. To by měl být kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.  
  
#### <a name="factory"></a>objekt pro vytváření  
 Název typu CLR objektu pro vytváření hostitele služby použít k vytvoření instance hostitele služby. Tento atribut je volitelné. Pokud tento parametr nezadáte, výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> se používá, které vrací instanci třídy <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Ladit  
 Určuje, zda služby Windows Communication Foundation (WCF) má kompilovat s ladicími symboly. `true` Pokud službu WCF má kompilovat s ladicími symboly; v opačném `false`.  
  
#### <a name="language"></a>Jazyk  
 Určuje jazyk použitý ke zkompilování všech vloženého kódu v rámci tohoto souboru (.svc). Hodnoty může představovat žádné. NET podporován jazyk, včetně C#, VB a Node.js na C#, Visual Basic .NET a JScript .NET. Tento atribut je volitelné.  
  
#### <a name="codebehind"></a>CodeBehind  
 Určuje zdrojový soubor, který implementuje webové služby XML, jakmile třídu, která implementuje webové služby XML nenachází ve stejném souboru nebyl byl zkompilován do sestavení a umístěn v adresáři \Bin.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.ServiceModel.ServiceHost> Použít k hostování služby je bod rozšiřitelnost v rámci programovací model Windows Communication Foundation (WCF). Vzor factory slouží k vytváření instancí <xref:System.ServiceModel.ServiceHost> protože se jedná, případně polymorfní typ, který by neměl hostitelské prostředí doložit přímo.  
  
 Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost>. Ale můžete zadat vlastní objekt pro vytváření (ten, který vrátí odvozené hostiteli) tak, že zadáte název vaší implementace objektu factory v typu CLR [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) – direktiva.  
  
 Pokud chcete používat vlastní služby vlastní objekt pro vytváření hostitele místo výchozí objekt pro vytváření, stačí zadat název typu ve [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) – direktiva následujícím způsobem:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Zachovat co nejlehčí factory implementace. Pokud máte velké množství vlastní logiky, je váš kód více opakovaně použitelný, když vložíte tuto logiku v hostiteli místo uvnitř objektu pro vytváření.  
  
 Například pro povolení koncového bodu technologie AJAX pro `MyService`, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu `Factory` atribut místo výchozího <xref:System.ServiceModel.Activation.ServiceHostFactory>v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy jako Následující příklad ukazuje.  
  
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
