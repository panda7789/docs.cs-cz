---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616238"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="f76fe-101">Kontrolní součty v jazyce XAML pro symboly změněné ze SHA1 na SHA256</span><span class="sxs-lookup"><span data-stu-id="f76fe-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="f76fe-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f76fe-102">Details</span></span>

<span data-ttu-id="f76fe-103">Pro podporu ladění pomocí sady Visual Studio modul runtime pracovního postupu generuje kontrolní součet pro soubor XAML pracovního postupu pomocí algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="f76fe-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="f76fe-104">V .NET Framework 4.6.2 a dřívějších verzích využívala hodnota hash kontrolního součtu workflowu algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS.</span><span class="sxs-lookup"><span data-stu-id="f76fe-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="f76fe-105">Počínaje .NET Framework 4,7 se výchozí algoritmus změnil na SHA1.</span><span class="sxs-lookup"><span data-stu-id="f76fe-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="f76fe-106">Počínaje .NET Framework 4,8 byl výchozí algoritmus změněn na SHA256.</span><span class="sxs-lookup"><span data-stu-id="f76fe-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f76fe-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="f76fe-107">Suggestion</span></span>

<span data-ttu-id="f76fe-108">Pokud váš kód nemůže načíst instance pracovního postupu nebo najít odpovídající symboly z důvodu chyby kontrolního součtu, zkuste nastavit `AppContext` přepínač "Switch.System". Activities. UseSHA1HashForDebuggerSymbols `true` .</span><span class="sxs-lookup"><span data-stu-id="f76fe-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="f76fe-109">V kódu:</span><span class="sxs-lookup"><span data-stu-id="f76fe-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="f76fe-110">Nebo v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="f76fe-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="f76fe-111">Name</span><span class="sxs-lookup"><span data-stu-id="f76fe-111">Name</span></span>    | <span data-ttu-id="f76fe-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f76fe-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f76fe-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f76fe-113">Scope</span></span>   | <span data-ttu-id="f76fe-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="f76fe-114">Minor</span></span>       |
| <span data-ttu-id="f76fe-115">Verze</span><span class="sxs-lookup"><span data-stu-id="f76fe-115">Version</span></span> | <span data-ttu-id="f76fe-116">4,8</span><span class="sxs-lookup"><span data-stu-id="f76fe-116">4.8</span></span>         |
| <span data-ttu-id="f76fe-117">Typ</span><span class="sxs-lookup"><span data-stu-id="f76fe-117">Type</span></span>    | <span data-ttu-id="f76fe-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="f76fe-118">Retargeting</span></span> |
