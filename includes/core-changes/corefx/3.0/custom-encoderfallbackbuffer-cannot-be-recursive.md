---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021672"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="0e458-101">Vlastní instance EncoderFallbackBuffer nemohou rekurzivně ustoupit</span><span class="sxs-lookup"><span data-stu-id="0e458-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="0e458-102">Vlastní <xref:System.Text.EncoderFallbackBuffer> instance nelze rekurzivně ustoupit.</span><span class="sxs-lookup"><span data-stu-id="0e458-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="0e458-103">Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek pořadí znaků, které je konvertibilní k cílovému kódování.</span><span class="sxs-lookup"><span data-stu-id="0e458-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="0e458-104">V opačném případě dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0e458-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e458-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="0e458-105">Change description</span></span>

<span data-ttu-id="0e458-106">Během operace překódování znak-bajt, runtime detekuje špatně vytvořené nebo nekonvertibilní Sekvence UTF-16 a poskytuje tyto znaky <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0e458-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0e458-107">Metoda `Fallback` určuje, které znaky by měly být nahrazeny původní nekonvertibilní data a tyto znaky jsou vyprázdněny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="0e458-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="0e458-108">Runtime se pak pokusí překódovat tyto substituční znaky do cílového kódování.</span><span class="sxs-lookup"><span data-stu-id="0e458-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="0e458-109">Pokud tato operace proběhne úspěšně, runtime pokračuje v překódování z místa, kde skončil v původním vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="0e458-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="0e458-110">V .NET Core Preview 7 a staršíverze <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vlastní implementace můžete vrátit sekvence znaků, které nejsou konvertibilní k cílovékódování.</span><span class="sxs-lookup"><span data-stu-id="0e458-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="0e458-111">Pokud nahrazené znaky nelze překódovat na cílové kódování, runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> vyvolá metodu znovu s <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> náhradní znaky, očekává, že metoda vrátí novou substituční sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0e458-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="0e458-112">Tento proces pokračuje, dokud runtime nakonec vidí dobře tvarované, konvertibilní nahrazení, nebo dokud není dosaženo maximálního počtu rekurzí.</span><span class="sxs-lookup"><span data-stu-id="0e458-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="0e458-113">Počínaje rozhraním .NET Core 3.0 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí vlastní implementace aplikace vrátit sekvence znaků, které jsou konvertibilní k cílovému kódování.</span><span class="sxs-lookup"><span data-stu-id="0e458-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="0e458-114">Pokud nahraditelné znaky nelze překódovat na cílové <xref:System.ArgumentException> kódování, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0e458-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="0e458-115">Runtime již nebude provádět rekurzivní volání <xref:System.Text.EncoderFallbackBuffer> do instance.</span><span class="sxs-lookup"><span data-stu-id="0e458-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="0e458-116">Toto chování platí pouze v případě, že jsou splněny všechny tři následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="0e458-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="0e458-117">Runtime detekuje špatně formátované Sekvence UTF-16 nebo UTF-16 sekvence, které nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="0e458-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="0e458-118">Byl <xref:System.Text.EncoderFallback> zadán vlastní.</span><span class="sxs-lookup"><span data-stu-id="0e458-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="0e458-119">Vlastní <xref:System.Text.EncoderFallback> pokusí nahradit nové špatně vytvořené nebo nekonvertibilní UTF-16 sekvence.</span><span class="sxs-lookup"><span data-stu-id="0e458-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e458-120">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0e458-120">Version introduced</span></span>

<span data-ttu-id="0e458-121">3.0</span><span class="sxs-lookup"><span data-stu-id="0e458-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e458-122">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0e458-122">Recommended action</span></span>

<span data-ttu-id="0e458-123">Většina vývojářů nemusí provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="0e458-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="0e458-124">Pokud aplikace používá <xref:System.Text.EncoderFallback> vlastní <xref:System.Text.EncoderFallbackBuffer> a třídy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ujistěte se, že implementace naplní záložní vyrovnávací paměti s dobře formátované <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> UTF-16 data, která je přímo konvertibilní na cílové kódování při metodě je poprvé vyvolána runtime.</span><span class="sxs-lookup"><span data-stu-id="0e458-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="0e458-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0e458-125">Category</span></span>

<span data-ttu-id="0e458-126">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="0e458-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e458-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0e458-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
