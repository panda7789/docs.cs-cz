---
title: MailAddressParser – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051347"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="507bd-102">MailAddressParser – třída</span><span class="sxs-lookup"><span data-stu-id="507bd-102">MailAddressParser class</span></span>

<span data-ttu-id="507bd-103">Analyzuje e-mailové adresy popsané v dokumentu RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="507bd-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="507bd-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="507bd-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="507bd-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="507bd-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="507bd-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="507bd-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="507bd-107">Metoda ParseAddress</span><span class="sxs-lookup"><span data-stu-id="507bd-107">ParseAddress method</span></span>

<span data-ttu-id="507bd-108">Analyzuje jednu e-mailovou adresu ze zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="507bd-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="507bd-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="507bd-109">Parameters</span></span>

<span data-ttu-id="507bd-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="507bd-110">`data` <xref:System.String></span></span>

<span data-ttu-id="507bd-111">Řetězec, který obsahuje e-mailovou adresu, která má být analyzována.</span><span class="sxs-lookup"><span data-stu-id="507bd-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="507bd-112">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="507bd-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="507bd-113">Platná e-mailová adresa</span><span class="sxs-lookup"><span data-stu-id="507bd-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="507bd-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="507bd-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="507bd-115">E-mailová adresa je neplatná.</span><span class="sxs-lookup"><span data-stu-id="507bd-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="507bd-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="507bd-116">Requirements</span></span>

<span data-ttu-id="507bd-117">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="507bd-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="507bd-118">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="507bd-118">**Assembly:** System (in System.dll)</span></span>
