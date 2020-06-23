---
title: HttpStatusDescription – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990337"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="d2c05-102">HttpStatusDescription – třída</span><span class="sxs-lookup"><span data-stu-id="d2c05-102">HttpStatusDescription class</span></span>

<span data-ttu-id="d2c05-103">Poskytuje standardní popisy stavu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2c05-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="d2c05-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="d2c05-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="d2c05-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d2c05-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d2c05-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2c05-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="d2c05-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="d2c05-107">Get method</span></span>

<span data-ttu-id="d2c05-108">Vrátí popis přidružený k zadanému kódu stavu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2c05-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="d2c05-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c05-109">Parameters</span></span>

<span data-ttu-id="d2c05-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="d2c05-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="d2c05-111">Stavový kód protokolu HTTP, například `404` .</span><span class="sxs-lookup"><span data-stu-id="d2c05-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="d2c05-112">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c05-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="d2c05-113">Popis stavu protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2c05-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2c05-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2c05-114">Requirements</span></span>

<span data-ttu-id="d2c05-115">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d2c05-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d2c05-116">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="d2c05-116">**Assembly:** System (in System.dll)</span></span>
