---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281293"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="5142a-101">Výchozí ActivityIdFormat je W3C.</span><span class="sxs-lookup"><span data-stu-id="5142a-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="5142a-102">Výchozí formát identifikátoru pro aktivitu ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) je nyní <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5142a-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5142a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5142a-103">Change description</span></span>

<span data-ttu-id="5142a-104">Formát ID aktivity W3C byl představen v .NET Core 3,0 jako alternativa k formátu hierarchického ID.</span><span class="sxs-lookup"><span data-stu-id="5142a-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="5142a-105">Pro zachování kompatibility ale formát W3C není výchozí, dokud neproběhne .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="5142a-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="5142a-106">Ve výchozím nastavení byla v rozhraní .NET 5,0 změněna, protože [formát W3C byl ratifikován](https://www.w3.org/TR/trace-context/) a byl získán v rámci více implementací jazyka.</span><span class="sxs-lookup"><span data-stu-id="5142a-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="5142a-107">Pokud se vaše aplikace zaměřuje na jinou platformu než .NET 5,0 nebo novější, bude se jednat o staré chování, kde <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> je výchozí formát.</span><span class="sxs-lookup"><span data-stu-id="5142a-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="5142a-108">Tato výchozí hodnota se vztahuje na platformy Net45 +, netstandard 1.1 + a netcoreapp (1. x, 2. x a 3. x).</span><span class="sxs-lookup"><span data-stu-id="5142a-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="5142a-109">V rozhraní .NET 5,0 a novějším <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> je nastaveno na <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5142a-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5142a-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5142a-110">Version introduced</span></span>

<span data-ttu-id="5142a-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="5142a-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5142a-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5142a-112">Recommended action</span></span>

<span data-ttu-id="5142a-113">Pokud je vaše aplikace nezávislá na identifikátor, který se používá pro distribuované trasování, není nutné provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="5142a-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="5142a-114">Knihovny jako ASP.NET Core a <xref:System.Net.Http.HttpClient> mohou využívat nebo rozšiřovat obě verze rozhraní <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="5142a-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="5142a-115">Pokud potřebujete interoperabilitu se stávajícími systémy nebo aktuální systémy spoléhají na formát identifikátoru, můžete zachovat staré chování nastavením <xref:System.Diagnostics.Activity.DefaultIdFormat> na <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5142a-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5142a-116">Alternativně můžete nastavit přepínač AppContext jedním ze tří způsobů:</span><span class="sxs-lookup"><span data-stu-id="5142a-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="5142a-117">V souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="5142a-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="5142a-118">V *runtimeconfig.jsv* souboru.</span><span class="sxs-lookup"><span data-stu-id="5142a-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="5142a-119">Prostřednictvím proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="5142a-119">Through an environment variable.</span></span>

  <span data-ttu-id="5142a-120">Nastavte `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` na `true` nebo 1.</span><span class="sxs-lookup"><span data-stu-id="5142a-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="5142a-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5142a-121">Category</span></span>

<span data-ttu-id="5142a-122">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="5142a-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5142a-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5142a-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
