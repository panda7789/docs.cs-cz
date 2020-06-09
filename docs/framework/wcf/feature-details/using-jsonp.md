---
title: Používání JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594956"
---
# <a name="using-jsonp"></a>Používání JSONP

Odsazení JSON (JSONP) je mechanismus, který umožňuje podporu skriptování mezi weby ve webových prohlížečích. JSONP je navrženo kolem schopnosti webových prohlížečů načíst skripty z lokality odlišnou od právě načteného načteného dokumentu. Mechanismus funguje tak, že naplní datovou část JSON pomocí uživatelsky definovaného názvu funkce zpětného volání, jak je znázorněno v následujícím příkladu.

```javascript
callback({"a" = \\"b\\"});
```

V předchozím příkladu datová část JSON `{"a" = \\"b\\"}` je zabalena ve volání funkce, `callback` . Funkce zpětného volání musí být na aktuální webové stránce již definována. Typ obsahu odpovědi JSONP je `application/javascript` .

JSONP není automaticky povoleno. Pokud ho chcete povolit, nastavte `javascriptCallbackEnabled` atribut na `true` jeden ze standardních koncových bodů http ( <xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint> ), jak je znázorněno v následujícím příkladu.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Název funkce zpětného volání lze zadat v proměnné dotazu nazvané zpětné volání, jak je znázorněno na následující adrese URL.

`http://baseaddress/Service/RestService?callback=functionName`

Při vyvolání služba odešle odpověď podobnou následující.

```javascript
functionName({"root":"Something"});
```  

Můžete také zadat název funkce zpětného volání, a to tak, že použijete na <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> třídu služby, jak je znázorněno v následujícím příkladu.

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

U výše uvedené služby je požadavek podobný následujícímu.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Při vyvolání služba odpoví následujícím.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Stavové kódy HTTP

Odpovědi JSONP se stavovým kódem HTTP jiným než 200 zahrnují druhý parametr s číselnou reprezentací stavového kódu HTTP, jak je znázorněno v následujícím příkladu.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Ověřování

Následující ověření jsou provedena, pokud je povoleno JSONP:

- Infrastruktura WCF vyvolá výjimku `javascriptCallback` , pokud je povolena, v žádosti se nachází parametr řetězce dotazu zpětného volání a formát odpovědi je nastaven na JSON.

- Pokud požadavek obsahuje parametr řetězce dotazu zpětného volání, ale operace není HTTP GET, parametr zpětného volání se ignoruje.

- Pokud je název zpětného volání `null` nebo prázdný řetězec, odpověď není formátována jako JSONP.

## <a name="see-also"></a>Viz také

- [Přehled programovacího modelu webových služeb HTTP WCF](wcf-web-http-programming-model-overview.md)
