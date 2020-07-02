---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614477"
---
### <a name="long-path-support"></a><span data-ttu-id="d456a-101">Podpora dlouhých cest</span><span class="sxs-lookup"><span data-stu-id="d456a-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="d456a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d456a-102">Details</span></span>

<span data-ttu-id="d456a-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se podporují dlouhé cesty (z až 32 znaků) a odeberou se omezení 260 znaků (nebo `MAX_PATH` ) na délkách cest. Pro aplikace, které jsou znovu kompilovány pro cílení na .NET Framework 4.6.2, cesty kódu, které dříve vyvolaly, <xref:System.IO.PathTooLongException?displayProperty=fullName> protože cesta překročila 260 znaků, bude nyní vyvolána <xref:System.IO.PathTooLongException?displayProperty=fullName> pouze za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="d456a-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="d456a-104">Délka cesty je větší než <xref:System.Int16.MaxValue> (32 767) znaků.</span><span class="sxs-lookup"><span data-stu-id="d456a-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="d456a-105">Operační systém vrátí `COR_E_PATHTOOLONG` nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="d456a-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="d456a-106">Pro aplikace, které cílí na .NET Framework 4.6.1 a starší verze, modul runtime automaticky vyvolá <xref:System.IO.PathTooLongException?displayProperty=fullName> vždy, když cesta překračuje 260 znaků.</span><span class="sxs-lookup"><span data-stu-id="d456a-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d456a-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="d456a-107">Suggestion</span></span>

<span data-ttu-id="d456a-108">U aplikací, které cílí na .NET Framework 4.6.2, se můžete rozhodnout, že podporu dlouhých cest nebudete mít, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :</span><span class="sxs-lookup"><span data-stu-id="d456a-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="d456a-109">Pro aplikace, které cílí na starší verze .NET Framework, ale běží na .NET Framework 4.6.2 nebo novější, se můžete rozhodnout pro podporu dlouhých cest tím, že do `<runtime>` části souboru přidáte následující `app.config` :</span><span class="sxs-lookup"><span data-stu-id="d456a-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="d456a-110">Name</span><span class="sxs-lookup"><span data-stu-id="d456a-110">Name</span></span>    | <span data-ttu-id="d456a-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d456a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d456a-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d456a-112">Scope</span></span>   | <span data-ttu-id="d456a-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="d456a-113">Minor</span></span>       |
| <span data-ttu-id="d456a-114">Verze</span><span class="sxs-lookup"><span data-stu-id="d456a-114">Version</span></span> | <span data-ttu-id="d456a-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d456a-115">4.6.2</span></span>       |
| <span data-ttu-id="d456a-116">Typ</span><span class="sxs-lookup"><span data-stu-id="d456a-116">Type</span></span>    | <span data-ttu-id="d456a-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="d456a-117">Retargeting</span></span> |
