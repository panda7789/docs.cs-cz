---
ms.openlocfilehash: 54ef49755dc0b9d1b821ae7999ab218626d455e1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556323"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="b88c7-101">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="b88c7-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="b88c7-102">Vlastní <xref:System.Text.EncoderFallbackBuffer> instance nemůžou vracet rekurzivně zpátky.</span><span class="sxs-lookup"><span data-stu-id="b88c7-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="b88c7-103">Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která je převoditelná na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="b88c7-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="b88c7-104">V opačném případě dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="b88c7-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b88c7-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b88c7-105">Change description</span></span>

<span data-ttu-id="b88c7-106">Během operace překódování znaků modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="b88c7-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b88c7-107">`Fallback`Metoda určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vynásobeny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="b88c7-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="b88c7-108">Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování.</span><span class="sxs-lookup"><span data-stu-id="b88c7-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="b88c7-109">Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="b88c7-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="b88c7-110">Dříve vlastní implementace nástroje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> mohou vracet sekvence znaků, které nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="b88c7-110">Previously, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="b88c7-111">Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ihned vyvolá metodu s náhradními znaky a očekává, že <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> Metoda vrátí novou sekvenci nahrazení.</span><span class="sxs-lookup"><span data-stu-id="b88c7-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="b88c7-112">Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.</span><span class="sxs-lookup"><span data-stu-id="b88c7-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="b88c7-113">Počínaje .NET Core 3,0, vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí vracet sekvence znaků, které jsou převoditelné na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="b88c7-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="b88c7-114">Pokud nahrazené znaky nelze překódovat do cílového kódování, <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b88c7-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="b88c7-115">Modul runtime již nebude do instance volat rekurzivní volání <xref:System.Text.EncoderFallbackBuffer> .</span><span class="sxs-lookup"><span data-stu-id="b88c7-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="b88c7-116">Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b88c7-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="b88c7-117">Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.</span><span class="sxs-lookup"><span data-stu-id="b88c7-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="b88c7-118">Byla zadána vlastní aplikace <xref:System.Text.EncoderFallback> .</span><span class="sxs-lookup"><span data-stu-id="b88c7-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="b88c7-119">Vlastní <xref:System.Text.EncoderFallback> pokusy o náhradu nové sekvence UTF-16, která se nesprávně vytvořila nebo nepřevoditelná.</span><span class="sxs-lookup"><span data-stu-id="b88c7-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b88c7-120">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b88c7-120">Version introduced</span></span>

<span data-ttu-id="b88c7-121">3.0</span><span class="sxs-lookup"><span data-stu-id="b88c7-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b88c7-122">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b88c7-122">Recommended action</span></span>

<span data-ttu-id="b88c7-123">Většina vývojářů nemusí podepisovat nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="b88c7-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="b88c7-124">Pokud aplikace používá vlastní <xref:System.Text.EncoderFallback> třídu a, ujistěte se, že <xref:System.Text.EncoderFallbackBuffer> implementace <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je přímo převoditelná na cílové kódování, když <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> je metoda poprvé vyvolána modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="b88c7-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="b88c7-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b88c7-125">Category</span></span>

<span data-ttu-id="b88c7-126">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="b88c7-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b88c7-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b88c7-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
