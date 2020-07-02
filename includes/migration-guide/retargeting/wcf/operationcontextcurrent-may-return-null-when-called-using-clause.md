---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614508"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext. Current může při volání klauzule using vracet hodnotu null.

#### <a name="details"></a>Podrobnosti

<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>může vracet `null` a <xref:System.NullReferenceException> může mít za následek splnění všech následujících podmínek:

- Hodnotu vlastnosti načtete <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> v metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .
- Vytvoříte instanci <xref:System.ServiceModel.OperationContextScope> objektu v `using` klauzuli.
- Hodnotu vlastnosti načtete <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> v rámci `using statement` . Příklad:

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a>Návrh

K vyřešení tohoto problému můžete postupovat takto:

- Upravte kód následujícím způsobem pro vytvoření instance nového objektu, který není `null` <xref:System.ServiceModel.OperationContext.Current%2A> objekt:

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- Nainstalujte nejnovější aktualizaci .NET Framework 4.6.2 nebo upgradujte na novější verzi .NET Framework. Tím se zakáže tok v nástroji <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> a obnoví se chování aplikací WCF v .NET Framework 4.6.1 a dřívějších verzích. Toto chování je konfigurovatelné. je ekvivalentní přidat následující nastavení aplikace do konfiguračního souboru:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    Pokud je tato změna nežádoucí a vaše aplikace závisí na kontextu spouštění mezi kontexty operací, můžete povolit tok následujícím způsobem:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
