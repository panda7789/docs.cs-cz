---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116347"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="45d3d-101">Microsoft.VisualBasic.Constants.vbNewLine je zastaralý</span><span class="sxs-lookup"><span data-stu-id="45d3d-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="45d3d-102">Konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> je [ \[označena jako zastaralá\] ](xref:System.ObsoleteAttribute) počínaje rozhraním .NET Core 3.0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="45d3d-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45d3d-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="45d3d-103">Version introduced</span></span>

<span data-ttu-id="45d3d-104">3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="45d3d-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="45d3d-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="45d3d-105">Change description</span></span>

<span data-ttu-id="45d3d-106">Počínaje rozhraním .NET Core 3.0 Preview 8 byl <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> atribut [Obsolete](xref:System.ObsoleteAttribute) použit na konstantu.</span><span class="sxs-lookup"><span data-stu-id="45d3d-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="45d3d-107">Použití konstanty vytváří upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="45d3d-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="45d3d-108">V rozhraní .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="45d3d-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="45d3d-109">Tato změna byla provedena pro podporu jazyka Visual Basic jako jazyk pro vývoj více platforem.</span><span class="sxs-lookup"><span data-stu-id="45d3d-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="45d3d-110">Konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine> je `\r\n`ekvivalentní , pořadí znaků nového řádku v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="45d3d-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="45d3d-111">V systémech založených na Unixu `\n`je znak nového řádku .</span><span class="sxs-lookup"><span data-stu-id="45d3d-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45d3d-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="45d3d-112">Recommended action</span></span>

<span data-ttu-id="45d3d-113">[Zpráva o atributu Zastaralé](xref:System.ObsoleteAttribute) pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> obsahuje následující doporučení:</span><span class="sxs-lookup"><span data-stu-id="45d3d-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="45d3d-114">Pro vrácení vozíku a <xref:Microsoft.VisualBasic.Constants.vbCrLf>posuv řádku použijte .</span><span class="sxs-lookup"><span data-stu-id="45d3d-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="45d3d-115">Pro novou linku aktuální platformy <xref:System.Environment.NewLine?displayProperty=nameWithType>použijte .</span><span class="sxs-lookup"><span data-stu-id="45d3d-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="45d3d-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="45d3d-116">Category</span></span>

<span data-ttu-id="45d3d-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45d3d-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45d3d-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="45d3d-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
