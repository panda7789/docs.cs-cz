---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617246"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="284b4-101">EncoderParameter ctor je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="284b4-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="284b4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="284b4-102">Details</span></span>

<span data-ttu-id="284b4-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor je zastaralý nyní a při použití zavede upozornění sestavení.</span><span class="sxs-lookup"><span data-stu-id="284b4-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="284b4-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="284b4-104">Suggestion</span></span>

<span data-ttu-id="284b4-105">I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> konstruktor bude i nadále fungovat, měli byste použít následující konstruktor, abyste zabránili zastaralému upozornění sestavení při opětovném kompilování kódu pomocí nástrojů .NET Framework 4,5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> .</span><span class="sxs-lookup"><span data-stu-id="284b4-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="284b4-106">Name</span><span class="sxs-lookup"><span data-stu-id="284b4-106">Name</span></span>    | <span data-ttu-id="284b4-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="284b4-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="284b4-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="284b4-108">Scope</span></span>   | <span data-ttu-id="284b4-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="284b4-109">Minor</span></span>       |
| <span data-ttu-id="284b4-110">Verze</span><span class="sxs-lookup"><span data-stu-id="284b4-110">Version</span></span> | <span data-ttu-id="284b4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="284b4-111">4.5</span></span>         |
| <span data-ttu-id="284b4-112">Typ</span><span class="sxs-lookup"><span data-stu-id="284b4-112">Type</span></span>    | <span data-ttu-id="284b4-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="284b4-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="284b4-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="284b4-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
