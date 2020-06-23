---
title: QuotedPairReader – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990329"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="cc19e-102">QuotedPairReader – třída</span><span class="sxs-lookup"><span data-stu-id="cc19e-102">QuotedPairReader class</span></span>

<span data-ttu-id="cc19e-103">Určuje, které znaky jsou v řetězci v uvozovkách v uvozovkách (uvozené pomocí řídicích znaků).</span><span class="sxs-lookup"><span data-stu-id="cc19e-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="cc19e-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="cc19e-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="cc19e-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="cc19e-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cc19e-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cc19e-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="cc19e-107">Metoda CountQuotedChars</span><span class="sxs-lookup"><span data-stu-id="cc19e-107">CountQuotedChars method</span></span>

<span data-ttu-id="cc19e-108">Spočítá počet po sobě jdoucích znaků v uvozovkách, včetně několika předchozích zpětných lomítek v zadaném řetězci.</span><span class="sxs-lookup"><span data-stu-id="cc19e-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="cc19e-109">Například při `a\\\b` zadání řetězce a indexu objektu se `4` Metoda vrátí `4` , protože `b` je v uvozovkách a tedy tři předchozí zpětná lomítka.</span><span class="sxs-lookup"><span data-stu-id="cc19e-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="cc19e-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc19e-110">Parameters</span></span>

- <span data-ttu-id="cc19e-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="cc19e-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="cc19e-112">Datový řetězec, ve kterém se mají počítat po sobě jdoucí znaky v uvozovkách</span><span class="sxs-lookup"><span data-stu-id="cc19e-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="cc19e-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="cc19e-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="cc19e-114">Pozice v zadaném řetězci až do a včetně, které by měly být započítány po sobě jdoucí uvozovky.</span><span class="sxs-lookup"><span data-stu-id="cc19e-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="cc19e-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="cc19e-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="cc19e-116">`true`povolení řídicích znaků znaků Unicode; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="cc19e-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="cc19e-117">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="cc19e-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="cc19e-118">`0`Pokud znak na zadaném indexu není uvozen řídicím znakem; v opačném případě počet po sobě jdoucích znaků v uvozovkách až do a včetně znaku na `index` .</span><span class="sxs-lookup"><span data-stu-id="cc19e-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="cc19e-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cc19e-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="cc19e-120">Byl nalezen řídicí znak Unicode, který však není povolen.</span><span class="sxs-lookup"><span data-stu-id="cc19e-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc19e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc19e-121">Requirements</span></span>

<span data-ttu-id="cc19e-122">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="cc19e-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="cc19e-123">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="cc19e-123">**Assembly:** System (in System.dll)</span></span>
