---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237329"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="410d5-101">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="410d5-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="410d5-102">Vlastní <xref:System.Text.EncoderFallbackBuffer> instancí nelze vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="410d5-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="410d5-103">Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která bude převoditelná na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="410d5-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="410d5-104">V opačném případě dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="410d5-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="410d5-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="410d5-105">Change description</span></span>

<span data-ttu-id="410d5-106">Během operace překódování po bajtech modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky metodě <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="410d5-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="410d5-107">Metoda `Fallback` určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vyprázdněny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="410d5-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="410d5-108">Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování.</span><span class="sxs-lookup"><span data-stu-id="410d5-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="410d5-109">Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="410d5-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="410d5-110">V rozhraní .NET Core Preview 7 a starších verzích mohou vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="410d5-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="410d5-111">Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime znovu vyvolá metodu <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> znovu s náhradními znaky a očekává, že metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vrátí novou sekvenci nahrazení.</span><span class="sxs-lookup"><span data-stu-id="410d5-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="410d5-112">Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.</span><span class="sxs-lookup"><span data-stu-id="410d5-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="410d5-113">Počínaje rozhraním .NET Core 3,0 musí vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které jsou převoditelné na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="410d5-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="410d5-114">Pokud nahrazené znaky nelze překódovat do cílového kódování, je vyvolána <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="410d5-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="410d5-115">Modul runtime již nebude provádět rekurzivní volání do instance <xref:System.Text.EncoderFallbackBuffer>.</span><span class="sxs-lookup"><span data-stu-id="410d5-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="410d5-116">Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="410d5-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="410d5-117">Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="410d5-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="410d5-118">Byl zadán vlastní <xref:System.Text.EncoderFallback>.</span><span class="sxs-lookup"><span data-stu-id="410d5-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="410d5-119">Vlastní <xref:System.Text.EncoderFallback> se pokusí nahradit novou sekvenci UTF-16 nesprávně vytvořenou nebo nepřevoditelnou.</span><span class="sxs-lookup"><span data-stu-id="410d5-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="410d5-120">Představená verze</span><span class="sxs-lookup"><span data-stu-id="410d5-120">Version introduced</span></span>

<span data-ttu-id="410d5-121">3,0</span><span class="sxs-lookup"><span data-stu-id="410d5-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="410d5-122">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="410d5-122">Recommended action</span></span>

<span data-ttu-id="410d5-123">Většina vývojářů nemusí podepisovat nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="410d5-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="410d5-124">Pokud aplikace používá vlastní třídu <xref:System.Text.EncoderFallback> a <xref:System.Text.EncoderFallbackBuffer>, ujistěte se, že implementace <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je přímo převoditelná na cílové kódování, pokud je metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> poprvé vyvolána rozhraním Runtime.</span><span class="sxs-lookup"><span data-stu-id="410d5-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="410d5-125">Category</span><span class="sxs-lookup"><span data-stu-id="410d5-125">Category</span></span>

<span data-ttu-id="410d5-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="410d5-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="410d5-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="410d5-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
