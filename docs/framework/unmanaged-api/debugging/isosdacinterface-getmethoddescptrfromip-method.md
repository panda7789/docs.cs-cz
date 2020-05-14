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
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396929"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="a149a-102">ISOSDacInterface:: GetMethodDescPtrFromIP – metoda</span><span class="sxs-lookup"><span data-stu-id="a149a-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="a149a-103">Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce.</span><span class="sxs-lookup"><span data-stu-id="a149a-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a149a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a149a-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="a149a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a149a-105">Parameters</span></span>

`ip`\
<span data-ttu-id="a149a-106">pro Adresa v rámci metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="a149a-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="a149a-107">mimo Adresa `MethodDesc` pro konkrétní metodu.</span><span class="sxs-lookup"><span data-stu-id="a149a-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="a149a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a149a-108">Remarks</span></span>

<span data-ttu-id="a149a-109">Poskytnutá metoda je součástí [ `ISOSDacInterface` rozhraní](isosdacinterface-interface.md) a odpovídá slotu 22 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="a149a-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a149a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a149a-110">Requirements</span></span>

<span data-ttu-id="a149a-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a149a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a149a-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="a149a-112">**Header:** None</span></span>  
<span data-ttu-id="a149a-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="a149a-113">**Library:** None</span></span>  
<span data-ttu-id="a149a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a149a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a149a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a149a-115">See also</span></span>

- [<span data-ttu-id="a149a-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="a149a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="a149a-117">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a149a-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
