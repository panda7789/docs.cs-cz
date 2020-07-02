---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616047"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="416ec-101">ObsoleteAttribute exportuje jako ObsoleteAttribute i DeprecatedAttribute ve scénářích WinMD</span><span class="sxs-lookup"><span data-stu-id="416ec-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="416ec-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="416ec-102">Details</span></span>

<span data-ttu-id="416ec-103">Když vytváříte knihovnu metadat systému Windows (soubor. winmd), <xref:System.ObsoleteAttribute?displayProperty=fullName> atribut je exportován jako i <xref:System.ObsoleteAttribute?displayProperty=fullName> [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span><span class="sxs-lookup"><span data-stu-id="416ec-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="416ec-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="416ec-104">Suggestion</span></span>

<span data-ttu-id="416ec-105">Opětovná kompilace stávajícího zdrojového kódu, který používá <xref:System.ObsoleteAttribute?displayProperty=fullName> atribut, může generovat upozornění při využívání kódu z C++/CX nebo JavaScript. nedoporučujeme <xref:System.ObsoleteAttribute?displayProperty=fullName> pro kód ve spravovaných sestaveních použít jak oba, tak [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) , což může vést k upozorněním sestavení.</span><span class="sxs-lookup"><span data-stu-id="416ec-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="416ec-106">Name</span><span class="sxs-lookup"><span data-stu-id="416ec-106">Name</span></span>    | <span data-ttu-id="416ec-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="416ec-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="416ec-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="416ec-108">Scope</span></span>   | <span data-ttu-id="416ec-109">Edge</span><span class="sxs-lookup"><span data-stu-id="416ec-109">Edge</span></span>        |
| <span data-ttu-id="416ec-110">Verze</span><span class="sxs-lookup"><span data-stu-id="416ec-110">Version</span></span> | <span data-ttu-id="416ec-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="416ec-111">4.5.1</span></span>       |
| <span data-ttu-id="416ec-112">Typ</span><span class="sxs-lookup"><span data-stu-id="416ec-112">Type</span></span>    | <span data-ttu-id="416ec-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="416ec-113">Retargeting</span></span> |
