---
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP – metoda'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421004"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="6dd10-102">ISOSDacInterface:: GetMethodDescPtrFromIP – metoda</span><span class="sxs-lookup"><span data-stu-id="6dd10-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="6dd10-103">Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce.</span><span class="sxs-lookup"><span data-stu-id="6dd10-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6dd10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dd10-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="6dd10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dd10-105">Parameters</span></span>

`ip`\
<span data-ttu-id="6dd10-106">pro Adresa v rámci metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="6dd10-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="6dd10-107">mimo Adresa `MethodDesc` pro konkrétní metodu.</span><span class="sxs-lookup"><span data-stu-id="6dd10-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="6dd10-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dd10-108">Remarks</span></span>

<span data-ttu-id="6dd10-109">Poskytnutá metoda je součástí [ `ISOSDacInterface` rozhraní](isosdacinterface-interface.md) a odpovídá slotu 22 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="6dd10-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dd10-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dd10-110">Requirements</span></span>

<span data-ttu-id="6dd10-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dd10-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6dd10-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="6dd10-112">**Header:** None</span></span>  
<span data-ttu-id="6dd10-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="6dd10-113">**Library:** None</span></span>  
<span data-ttu-id="6dd10-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6dd10-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6dd10-115">See also</span></span>

- [<span data-ttu-id="6dd10-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="6dd10-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="6dd10-117">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6dd10-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
