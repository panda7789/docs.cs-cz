---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234644"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="11dca-101">EncoderParameter ctor je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="11dca-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="11dca-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="11dca-102">Details</span></span>|<span data-ttu-id="11dca-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor je nyní zastaralé a budou zavedeny upozornění sestavení, pokud se používá.</span><span class="sxs-lookup"><span data-stu-id="11dca-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="11dca-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="11dca-104">Suggestion</span></span>|<span data-ttu-id="11dca-105">I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>konstruktoru bude pokračovat v práci, následující konstruktor by měl místo toho použít při opětovné kompilaci kódu pomocí nástroje rozhraní .NET Framework 4.5, aby upozornění zastaralé sestavení: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="11dca-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="11dca-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="11dca-106">Scope</span></span>|<span data-ttu-id="11dca-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="11dca-107">Minor</span></span>|
|<span data-ttu-id="11dca-108">Version</span><span class="sxs-lookup"><span data-stu-id="11dca-108">Version</span></span>|<span data-ttu-id="11dca-109">4.5</span><span class="sxs-lookup"><span data-stu-id="11dca-109">4.5</span></span>|
|<span data-ttu-id="11dca-110">Type</span><span class="sxs-lookup"><span data-stu-id="11dca-110">Type</span></span>|<span data-ttu-id="11dca-111">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="11dca-111">Retargeting</span></span>|
|<span data-ttu-id="11dca-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="11dca-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
