---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614550"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="b92d8-101">Kontrolní součty pracovního postupu se změnily z MD5 na SHA1.</span><span class="sxs-lookup"><span data-stu-id="b92d8-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="b92d8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b92d8-102">Details</span></span>

<span data-ttu-id="b92d8-103">Pro podporu ladění pomocí sady Visual Studio modul runtime pracovního postupu generuje kontrolní součet pro instanci pracovního postupu pomocí algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="b92d8-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="b92d8-104">V .NET Framework 4.6.2 a dřívějších verzích využívala hodnota hash kontrolního součtu workflowu algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS.</span><span class="sxs-lookup"><span data-stu-id="b92d8-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="b92d8-105">Počínaje .NET Framework 4,7 je algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="b92d8-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="b92d8-106">Pokud váš kód trval tyto kontrolní součty, budou nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b92d8-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b92d8-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="b92d8-107">Suggestion</span></span>

<span data-ttu-id="b92d8-108">Pokud váš kód nemůže načíst instance pracovního postupu z důvodu chyby kontrolního součtu, zkuste nastavit `AppContext` přepínač &quot;Switch.System. Activities. UseMD5ForWFDebugger &quot; na hodnotu true. V kódu:</span><span class="sxs-lookup"><span data-stu-id="b92d8-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="b92d8-109">Nebo v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="b92d8-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="b92d8-110">Name</span><span class="sxs-lookup"><span data-stu-id="b92d8-110">Name</span></span>    | <span data-ttu-id="b92d8-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b92d8-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b92d8-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b92d8-112">Scope</span></span>   | <span data-ttu-id="b92d8-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="b92d8-113">Minor</span></span>       |
| <span data-ttu-id="b92d8-114">Verze</span><span class="sxs-lookup"><span data-stu-id="b92d8-114">Version</span></span> | <span data-ttu-id="b92d8-115">4,7</span><span class="sxs-lookup"><span data-stu-id="b92d8-115">4.7</span></span>         |
| <span data-ttu-id="b92d8-116">Typ</span><span class="sxs-lookup"><span data-stu-id="b92d8-116">Type</span></span>    | <span data-ttu-id="b92d8-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b92d8-117">Retargeting</span></span> |
