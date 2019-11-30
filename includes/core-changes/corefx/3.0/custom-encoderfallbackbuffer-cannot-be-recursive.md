---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568180"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="6a29f-101">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="6a29f-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="6a29f-102">Vlastní instance <xref:System.Text.EncoderFallbackBuffer> nemohou vracet rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="6a29f-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="6a29f-103">Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která bude převoditelná na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a29f-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="6a29f-104">V opačném případě dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="6a29f-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6a29f-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="6a29f-105">Change description</span></span>

<span data-ttu-id="6a29f-106">Během operace překódování znaků modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky metodě <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a29f-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6a29f-107">Metoda `Fallback` určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vynásobeny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="6a29f-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="6a29f-108">Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování.</span><span class="sxs-lookup"><span data-stu-id="6a29f-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="6a29f-109">Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="6a29f-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="6a29f-110">V rozhraní .NET Core Preview 7 a starších verzích mohou vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a29f-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="6a29f-111">Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime vyvolá metodu <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> znovu s náhradními znaky a očekává, že <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metoda vrátí novou sekvenci nahrazení.</span><span class="sxs-lookup"><span data-stu-id="6a29f-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="6a29f-112">Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.</span><span class="sxs-lookup"><span data-stu-id="6a29f-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="6a29f-113">Počínaje rozhraním .NET Core 3,0 musí vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které jsou převoditelné na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a29f-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="6a29f-114">Pokud nahrazené znaky nelze překódovat do cílového kódování, je vyvolána <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="6a29f-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="6a29f-115">Modul runtime již nebude provádět rekurzivní volání do instance <xref:System.Text.EncoderFallbackBuffer>.</span><span class="sxs-lookup"><span data-stu-id="6a29f-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="6a29f-116">Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="6a29f-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="6a29f-117">Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a29f-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="6a29f-118">Byl zadán vlastní <xref:System.Text.EncoderFallback>.</span><span class="sxs-lookup"><span data-stu-id="6a29f-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="6a29f-119">Vlastní <xref:System.Text.EncoderFallback> se pokusí nahradit novou sekvenci UTF-16 ve špatném formátu nebo nepřevoditelnou.</span><span class="sxs-lookup"><span data-stu-id="6a29f-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6a29f-120">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6a29f-120">Version introduced</span></span>

<span data-ttu-id="6a29f-121">3,0</span><span class="sxs-lookup"><span data-stu-id="6a29f-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6a29f-122">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6a29f-122">Recommended action</span></span>

<span data-ttu-id="6a29f-123">Většina vývojářů nemusí podepisovat nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="6a29f-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="6a29f-124">Pokud aplikace používá vlastní <xref:System.Text.EncoderFallback> a <xref:System.Text.EncoderFallbackBuffer> třídu, ujistěte se, že implementace <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je přímo převoditelná na cílové kódování, pokud je metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> poprvé vyvolána modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="6a29f-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="6a29f-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6a29f-125">Category</span></span>

<span data-ttu-id="6a29f-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6a29f-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6a29f-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6a29f-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
