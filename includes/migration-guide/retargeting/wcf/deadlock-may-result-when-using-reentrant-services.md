---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614525"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="99612-101">Při použití přidaných služeb může dojít k zablokování.</span><span class="sxs-lookup"><span data-stu-id="99612-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="99612-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="99612-102">Details</span></span>

<span data-ttu-id="99612-103">Zablokování může mít za následek předanou službu, která omezí instance služby na jeden podproces spuštění v čase.</span><span class="sxs-lookup"><span data-stu-id="99612-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="99612-104">Služby náchylné k tomuto problému budou mít <xref:System.ServiceModel.ServiceBehaviorAttribute> v kódu následující:</span><span class="sxs-lookup"><span data-stu-id="99612-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="99612-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="99612-105">Suggestion</span></span>

<span data-ttu-id="99612-106">K vyřešení tohoto problému můžete postupovat takto:</span><span class="sxs-lookup"><span data-stu-id="99612-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="99612-107">Nastavte režim souběžnosti služby na <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> nebo &lt; System. ServiceModel. ConcurrencyMode. Multiple? DisplayProperty = nameWithType &gt; .</span><span class="sxs-lookup"><span data-stu-id="99612-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="99612-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="99612-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="99612-109">Nainstalujte nejnovější aktualizaci .NET Framework 4.6.2 nebo upgradujte na novější verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99612-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="99612-110">Tím se zakáže tok v nástroji <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="99612-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99612-111">Toto chování je konfigurovatelné. je ekvivalentní přidat následující nastavení aplikace do konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="99612-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="99612-112">Hodnota `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` by nikdy neměla být nastavená na `false` pro znovu vstupující služby.</span><span class="sxs-lookup"><span data-stu-id="99612-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="99612-113">Name</span><span class="sxs-lookup"><span data-stu-id="99612-113">Name</span></span>    | <span data-ttu-id="99612-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="99612-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="99612-115">Rozsah</span><span class="sxs-lookup"><span data-stu-id="99612-115">Scope</span></span>   | <span data-ttu-id="99612-116">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="99612-116">Minor</span></span>       |
| <span data-ttu-id="99612-117">Verze</span><span class="sxs-lookup"><span data-stu-id="99612-117">Version</span></span> | <span data-ttu-id="99612-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="99612-118">4.6.2</span></span>       |
| <span data-ttu-id="99612-119">Typ</span><span class="sxs-lookup"><span data-stu-id="99612-119">Type</span></span>    | <span data-ttu-id="99612-120">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="99612-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="99612-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="99612-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
