---
title: MailBnfHelper – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990328"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="fc87e-102">MailBnfHelper – třída</span><span class="sxs-lookup"><span data-stu-id="fc87e-102">MailBnfHelper class</span></span>

<span data-ttu-id="fc87e-103">Obsahuje metody nástrojů pro analýzu řetězců ve formátu internetových zpráv.</span><span class="sxs-lookup"><span data-stu-id="fc87e-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="fc87e-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="fc87e-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="fc87e-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="fc87e-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fc87e-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc87e-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="fc87e-107">Pole Ascii7bitMaxValue</span><span class="sxs-lookup"><span data-stu-id="fc87e-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="fc87e-108">Představuje maximální hodnotu 7 bitů ASCII.</span><span class="sxs-lookup"><span data-stu-id="fc87e-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="fc87e-109">Pole atext</span><span class="sxs-lookup"><span data-stu-id="fc87e-109">Atext field</span></span>

<span data-ttu-id="fc87e-110">Představuje znaky povolené ve atomech.</span><span class="sxs-lookup"><span data-stu-id="fc87e-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="fc87e-111">Pole CR</span><span class="sxs-lookup"><span data-stu-id="fc87e-111">CR field</span></span>

<span data-ttu-id="fc87e-112">Představuje znak návratu na začátek řádku.</span><span class="sxs-lookup"><span data-stu-id="fc87e-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="fc87e-113">Pole CTEXT</span><span class="sxs-lookup"><span data-stu-id="fc87e-113">Ctext field</span></span>

<span data-ttu-id="fc87e-114">Představuje znaky povolené v komentářích.</span><span class="sxs-lookup"><span data-stu-id="fc87e-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="fc87e-115">Pole s tečkou</span><span class="sxs-lookup"><span data-stu-id="fc87e-115">Dot field</span></span>

<span data-ttu-id="fc87e-116">Představuje znak úplného zastavení ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="fc87e-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="fc87e-117">Pole EndComment</span><span class="sxs-lookup"><span data-stu-id="fc87e-117">EndComment field</span></span>

<span data-ttu-id="fc87e-118">Představuje znak, který určuje konec komentáře.</span><span class="sxs-lookup"><span data-stu-id="fc87e-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="fc87e-119">Pole LF</span><span class="sxs-lookup"><span data-stu-id="fc87e-119">LF field</span></span>

<span data-ttu-id="fc87e-120">Představuje znak kanálu čáry.</span><span class="sxs-lookup"><span data-stu-id="fc87e-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="fc87e-121">Pole prostor</span><span class="sxs-lookup"><span data-stu-id="fc87e-121">Space field</span></span>

<span data-ttu-id="fc87e-122">Představuje znak mezery.</span><span class="sxs-lookup"><span data-stu-id="fc87e-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="fc87e-123">Pole StartComment</span><span class="sxs-lookup"><span data-stu-id="fc87e-123">StartComment field</span></span>

<span data-ttu-id="fc87e-124">Představuje znak, který určuje začátek komentáře.</span><span class="sxs-lookup"><span data-stu-id="fc87e-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="fc87e-125">Pole karty</span><span class="sxs-lookup"><span data-stu-id="fc87e-125">Tab field</span></span>

<span data-ttu-id="fc87e-126">Představuje znak tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="fc87e-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="fc87e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc87e-127">Requirements</span></span>

<span data-ttu-id="fc87e-128">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="fc87e-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="fc87e-129">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="fc87e-129">**Assembly:** System (in System.dll)</span></span>
