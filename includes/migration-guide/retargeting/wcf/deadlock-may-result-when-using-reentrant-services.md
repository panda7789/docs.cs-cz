---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614525"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Při použití přidaných služeb může dojít k zablokování.

#### <a name="details"></a>Podrobnosti

Zablokování může mít za následek předanou službu, která omezí instance služby na jeden podproces spuštění v čase. Služby náchylné k tomuto problému budou mít <xref:System.ServiceModel.ServiceBehaviorAttribute> v kódu následující:

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a>Návrh

K vyřešení tohoto problému můžete postupovat takto:

- Nastavte režim souběžnosti služby na <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> nebo &lt; System. ServiceModel. ConcurrencyMode. Multiple? DisplayProperty = nameWithType &gt; . Příklad:

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- Nainstalujte nejnovější aktualizaci .NET Framework 4.6.2 nebo upgradujte na novější verzi .NET Framework. Tím se zakáže tok v nástroji <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> . Toto chování je konfigurovatelné. je ekvivalentní přidat následující nastavení aplikace do konfiguračního souboru:

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

Hodnota `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` by nikdy neměla být nastavená na `false` pro znovu vstupující služby.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
