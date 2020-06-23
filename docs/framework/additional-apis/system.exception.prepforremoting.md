---
title: Exception. PrepForRemoting – metoda (System)
description: Přečtěte si metodu Exception. PrepForRemoting v rozhraní .NET. Metoda přidá do zprávy trasování zásobníku na straně serveru před tím, než je výjimka znovu vyvolána v klientovi.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105263"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="1f1d2-104">Exception.PrepForRemoting – metoda</span><span class="sxs-lookup"><span data-stu-id="1f1d2-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="1f1d2-105">Zachovává trasování zásobníku na straně serveru tím, že ho připojí ke zprávě předtím, než se výjimka znovu vyvolá na webu klientského volání.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="1f1d2-106">Návraty</span><span class="sxs-lookup"><span data-stu-id="1f1d2-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="1f1d2-107">Tato <xref:System.Exception> instance.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f1d2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f1d2-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1f1d2-109">`Exception.PrepForRemoting`Metoda je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1f1d2-110">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f1d2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f1d2-111">Requirements</span></span>

<span data-ttu-id="1f1d2-112">**Obor názvů:**<xref:System></span><span class="sxs-lookup"><span data-stu-id="1f1d2-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="1f1d2-113">**Assembly:** mscorlib.dll (v mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="1f1d2-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="1f1d2-114">**Verze .NET Framework:** K dispozici od verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-114">**.NET Framework versions:** Available since 1.0.</span></span>
