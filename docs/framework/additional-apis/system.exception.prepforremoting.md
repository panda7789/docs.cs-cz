---
title: Exception. PrepForRemoting – metoda (System)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214888"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="bb2ea-102">Exception.PrepForRemoting – metoda</span><span class="sxs-lookup"><span data-stu-id="bb2ea-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="bb2ea-103">Zachovává trasování zásobníku na straně serveru tím, že ho připojí ke zprávě předtím, než se výjimka znovu vyvolá na webu klientského volání.</span><span class="sxs-lookup"><span data-stu-id="bb2ea-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="bb2ea-104">Vrací</span><span class="sxs-lookup"><span data-stu-id="bb2ea-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="bb2ea-105">Tato <xref:System.Exception> instance.</span><span class="sxs-lookup"><span data-stu-id="bb2ea-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb2ea-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb2ea-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bb2ea-107">Metoda `Exception.PrepForRemoting` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="bb2ea-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bb2ea-108">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bb2ea-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb2ea-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb2ea-109">Requirements</span></span>

<span data-ttu-id="bb2ea-110">**Obor názvů:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="bb2ea-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="bb2ea-111">**Sestavení:** mscorlib. dll (v mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="bb2ea-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="bb2ea-112">**Verze .NET Framework:** K dispozici od verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="bb2ea-112">**.NET Framework versions:** Available since 1.0.</span></span>
