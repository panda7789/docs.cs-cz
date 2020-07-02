---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614508"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="3e2e3-101">OperationContext. Current může při volání klauzule using vracet hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3e2e3-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="3e2e3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3e2e3-102">Details</span></span>

<span data-ttu-id="3e2e3-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>může vracet `null` a <xref:System.NullReferenceException> může mít za následek splnění všech následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="3e2e3-104">Hodnotu vlastnosti načtete <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> v metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="3e2e3-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="3e2e3-105">Vytvoříte instanci <xref:System.ServiceModel.OperationContextScope> objektu v `using` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3e2e3-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="3e2e3-106">Hodnotu vlastnosti načtete <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> v rámci `using statement` .</span><span class="sxs-lookup"><span data-stu-id="3e2e3-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="3e2e3-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="3e2e3-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="3e2e3-108">Suggestion</span></span>

<span data-ttu-id="3e2e3-109">K vyřešení tohoto problému můžete postupovat takto:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="3e2e3-110">Upravte kód následujícím způsobem pro vytvoření instance nového objektu, který není `null` <xref:System.ServiceModel.OperationContext.Current%2A> objekt:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="3e2e3-111">Nainstalujte nejnovější aktualizaci .NET Framework 4.6.2 nebo upgradujte na novější verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e2e3-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="3e2e3-112">Tím se zakáže tok v nástroji <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> a obnoví se chování aplikací WCF v .NET Framework 4.6.1 a dřívějších verzích.</span><span class="sxs-lookup"><span data-stu-id="3e2e3-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="3e2e3-113">Toto chování je konfigurovatelné. je ekvivalentní přidat následující nastavení aplikace do konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="3e2e3-114">Pokud je tato změna nežádoucí a vaše aplikace závisí na kontextu spouštění mezi kontexty operací, můžete povolit tok následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3e2e3-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="3e2e3-115">Name</span><span class="sxs-lookup"><span data-stu-id="3e2e3-115">Name</span></span>    | <span data-ttu-id="3e2e3-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3e2e3-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e2e3-117">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3e2e3-117">Scope</span></span>   | <span data-ttu-id="3e2e3-118">Edge</span><span class="sxs-lookup"><span data-stu-id="3e2e3-118">Edge</span></span>        |
| <span data-ttu-id="3e2e3-119">Verze</span><span class="sxs-lookup"><span data-stu-id="3e2e3-119">Version</span></span> | <span data-ttu-id="3e2e3-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3e2e3-120">4.6.2</span></span>       |
| <span data-ttu-id="3e2e3-121">Typ</span><span class="sxs-lookup"><span data-stu-id="3e2e3-121">Type</span></span>    | <span data-ttu-id="3e2e3-122">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="3e2e3-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3e2e3-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3e2e3-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
