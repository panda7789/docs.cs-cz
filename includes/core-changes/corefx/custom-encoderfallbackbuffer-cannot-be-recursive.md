---
ms.openlocfilehash: 4075eadf7cfb39c913b7657d43335bae5497deff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217050"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="93bff-101">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="93bff-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="93bff-102">Vlastní <xref:System.Text.EncoderFallbackBuffer> instance nemůžou vracet rekurzivně zpátky.</span><span class="sxs-lookup"><span data-stu-id="93bff-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="93bff-103">Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která je převoditelná na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="93bff-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="93bff-104">V opačném případě dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="93bff-104">Otherwise, an exception occurs.</span></span>

#### <a name="details"></a><span data-ttu-id="93bff-105">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="93bff-105">Details</span></span>

<span data-ttu-id="93bff-106">Během operace překódování znaků modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="93bff-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="93bff-107">Metoda určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vynásobeny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce. `Fallback`</span><span class="sxs-lookup"><span data-stu-id="93bff-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="93bff-108">Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování.</span><span class="sxs-lookup"><span data-stu-id="93bff-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="93bff-109">Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="93bff-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="93bff-110">V .NET Core Preview 7 a starších verzích mohou vlastní implementace pro <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="93bff-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="93bff-111">Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime ihned vyvolá <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodu s náhradními znaky a očekává, že <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> Metoda vrátí novou sekvenci nahrazení.</span><span class="sxs-lookup"><span data-stu-id="93bff-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="93bff-112">Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.</span><span class="sxs-lookup"><span data-stu-id="93bff-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="93bff-113">Počínaje .NET Core 3,0, vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí vracet sekvence znaků, které jsou převoditelné na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="93bff-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="93bff-114">Pokud nahrazené znaky nelze překódovat do cílového kódování, <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="93bff-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="93bff-115">Modul runtime již nebude do <xref:System.Text.EncoderFallbackBuffer> instance volat rekurzivní volání.</span><span class="sxs-lookup"><span data-stu-id="93bff-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="93bff-116">Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="93bff-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="93bff-117">Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="93bff-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="93bff-118">Byla zadána <xref:System.Text.EncoderFallback> vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="93bff-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="93bff-119">Vlastní <xref:System.Text.EncoderFallback> pokusy o náhradu nové sekvence UTF-16, která se nesprávně vytvořila nebo nepřevoditelná.</span><span class="sxs-lookup"><span data-stu-id="93bff-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="93bff-120">Představená verze</span><span class="sxs-lookup"><span data-stu-id="93bff-120">Version introduced</span></span>

<span data-ttu-id="93bff-121">3.0</span><span class="sxs-lookup"><span data-stu-id="93bff-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="93bff-122">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="93bff-122">Recommended action</span></span>

<span data-ttu-id="93bff-123">Většina vývojářů nemusí podepisovat nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="93bff-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="93bff-124">Pokud <xref:System.Text.EncoderFallback> aplikace používá vlastní třídu a <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> , ujistěte se, že implementace naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> přímo převoditelná na cílové kódování v případě metody. je nejprve vyvolána modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="93bff-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="93bff-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="93bff-125">Category</span></span>

<span data-ttu-id="93bff-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="93bff-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="93bff-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="93bff-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
