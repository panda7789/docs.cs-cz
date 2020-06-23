---
title: MailAddressParser – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990333"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="d5637-102">MailAddressParser – třída</span><span class="sxs-lookup"><span data-stu-id="d5637-102">MailAddressParser class</span></span>

<span data-ttu-id="d5637-103">Analyzuje e-mailové adresy popsané v dokumentu RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="d5637-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="d5637-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="d5637-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="d5637-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d5637-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d5637-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d5637-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="d5637-107">Metoda ParseAddress</span><span class="sxs-lookup"><span data-stu-id="d5637-107">ParseAddress method</span></span>

<span data-ttu-id="d5637-108">Analyzuje jednu e-mailovou adresu ze zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="d5637-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="d5637-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5637-109">Parameters</span></span>

<span data-ttu-id="d5637-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="d5637-110">`data` <xref:System.String></span></span>

<span data-ttu-id="d5637-111">Řetězec, který obsahuje e-mailovou adresu, která má být analyzována.</span><span class="sxs-lookup"><span data-stu-id="d5637-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="d5637-112">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="d5637-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="d5637-113">Platná e-mailová adresa</span><span class="sxs-lookup"><span data-stu-id="d5637-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="d5637-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="d5637-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="d5637-115">E-mailová adresa je neplatná.</span><span class="sxs-lookup"><span data-stu-id="d5637-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5637-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5637-116">Requirements</span></span>

<span data-ttu-id="d5637-117">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d5637-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d5637-118">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="d5637-118">**Assembly:** System (in System.dll)</span></span>
