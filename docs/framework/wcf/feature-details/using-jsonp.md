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
# <a name="using-jsonp"></a><span data-ttu-id="9d8ae-102">Používání JSONP</span><span class="sxs-lookup"><span data-stu-id="9d8ae-102">Using JSONP</span></span>

<span data-ttu-id="9d8ae-103">Odsazení JSON (JSONP) je mechanismus, který umožňuje podporu webů skriptování v webových prohlížečů.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="9d8ae-104">JSONP je uspořádaná kolem webových prohlížečů schopnost načíst skripty z lokality rozdílné aktuální načtený dokument byla načtena z.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="9d8ae-105">Tento mechanismus funguje odsazením datové části JSON s názvem uživatelské zpětné volání funkce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="9d8ae-106">V předchozím příkladu datové části JSON `{"a" = \\"b\\"}`, je uzavřen do volání funkce `callback`.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="9d8ae-107">Funkce zpětného volání musí být definovány již v aktuální webové stránky.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="9d8ae-108">Typ obsahu odpovědi JSONP `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="9d8ae-109">JSONP není povolené automaticky.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="9d8ae-110">Chcete-li ji povolit, nastavte `javascriptCallbackEnabled` atribut `true` na jednom ze standardních koncových bodů protokolu HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="9d8ae-111">Název funkce zpětného volání může být zadán v dotazu proměnné s názvem zpětného volání, jak je znázorněno v následující adresu URL.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="9d8ae-112">Po vyvolání službu odešle odpověď podobně jako tento.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="9d8ae-113">Můžete také zadat název funkce zpětného volání při použití <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> k třídě služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="9d8ae-114">Pro službu uvedený výše žádost o vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="9d8ae-115">Po vyvolání službu odpoví následující.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="9d8ae-116">Stavové kódy HTTP</span><span class="sxs-lookup"><span data-stu-id="9d8ae-116">HTTP Status Codes</span></span>

<span data-ttu-id="9d8ae-117">JSONP odpovědi s stavové kódy HTTP než 200 zahrnují druhý parametr s číselnému znázornění stavový kód protokolu HTTP, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="9d8ae-118">Ověření</span><span class="sxs-lookup"><span data-stu-id="9d8ae-118">Validations</span></span>

<span data-ttu-id="9d8ae-119">Pokud je povolen formát JSONP, jsou prováděny následující ověření:</span><span class="sxs-lookup"><span data-stu-id="9d8ae-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="9d8ae-120">Infrastruktura WCF vyvolá výjimku, pokud `javascriptCallback` je povoleno, je k dispozici v požadavku parametr řetězce dotazu zpětného volání a formát odpovědi je nastaven na JSON.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="9d8ae-121">Pokud požadavek obsahuje parametr řetězce dotazu zpětného volání, ale není operaci HTTP GET, parametr zpětné volání je ignorován.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="9d8ae-122">Pokud je název zpětné volání `null` prázdný řetězec odpovědi není naformátovaná jako JSONP.</span><span class="sxs-lookup"><span data-stu-id="9d8ae-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d8ae-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d8ae-123">See also</span></span>

[<span data-ttu-id="9d8ae-124">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="9d8ae-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
