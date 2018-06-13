---
title: Používání JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 55f90c37dc4e94653f2233371a044a2f019b59a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497981"
---
# <a name="using-jsonp"></a>Používání JSONP

Odsazení JSON (JSONP) je mechanismus, který umožňuje podporu webů skriptování v webových prohlížečů. JSONP je uspořádaná kolem webových prohlížečů schopnost načíst skripty z lokality rozdílné aktuální načtený dokument byla načtena z. Tento mechanismus funguje odsazením datové části JSON s názvem uživatelské zpětné volání funkce, jak je znázorněno v následujícím příkladu.

```javascript
callback({"a" = \\"b\\"});
```

V předchozím příkladu datové části JSON `{"a" = \\"b\\"}`, je uzavřen do volání funkce `callback`. Funkce zpětného volání musí být definovány již v aktuální webové stránky. Typ obsahu odpovědi JSONP `application/javascript`.

JSONP není povolené automaticky. Chcete-li ji povolit, nastavte `javascriptCallbackEnabled` atribut `true` na jednom ze standardních koncových bodů protokolu HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak je znázorněno v následujícím příkladu.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Název funkce zpětného volání může být zadán v dotazu proměnné s názvem zpětného volání, jak je znázorněno v následující adresu URL.

`http://baseaddress/Service/RestService?callback=functionName`

Po vyvolání službu odešle odpověď podobně jako tento.

```javascript
functionName({"root":"Something"});
```  

Můžete také zadat název funkce zpětného volání při použití <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> k třídě služby, jak je znázorněno v následujícím příkladu.

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

Pro službu uvedený výše žádost o vypadá takto.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Po vyvolání službu odpoví následující.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Stavové kódy HTTP

JSONP odpovědi s stavové kódy HTTP než 200 zahrnují druhý parametr s číselnému znázornění stavový kód protokolu HTTP, jak je znázorněno v následujícím příkladu.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Ověření

Pokud je povolen formát JSONP, jsou prováděny následující ověření:

- Infrastruktura WCF vyvolá výjimku, pokud `javascriptCallback` je povoleno, je k dispozici v požadavku parametr řetězce dotazu zpětného volání a formát odpovědi je nastaven na JSON.

- Pokud požadavek obsahuje parametr řetězce dotazu zpětného volání, ale není operaci HTTP GET, parametr zpětné volání je ignorován.

- Pokud je název zpětné volání `null` prázdný řetězec odpovědi není naformátovaná jako JSONP.

## <a name="see-also"></a>Viz také

[Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
