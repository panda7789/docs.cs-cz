---
title: ISOSDacInterface::GetMethodDescPtrFromIP – metoda
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
ms.openlocfilehash: 82c4531ac16e8b4bf7ac45bc01eb7128b9507ab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922756"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="326a1-102">ISOSDacInterface::GetMethodDescPtrFromIP – metoda</span><span class="sxs-lookup"><span data-stu-id="326a1-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="326a1-103">Načte ukazatel MethodDesc odpovídající metodu obsahující uvedené instrukce nativní adresu.</span><span class="sxs-lookup"><span data-stu-id="326a1-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="326a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="326a1-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="326a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="326a1-105">Parameters</span></span>

`ip`\
<span data-ttu-id="326a1-106">[in] Adresy v rámci metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="326a1-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="326a1-107">[out] Adresa `MethodDesc` pro konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="326a1-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="326a1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="326a1-108">Remarks</span></span>

<span data-ttu-id="326a1-109">Zadaná metoda je součástí [ `ISOSDacInterface` rozhraní](isosdacinterface-interface.md) a odpovídá 21 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="326a1-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="326a1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="326a1-110">Requirements</span></span>

<span data-ttu-id="326a1-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="326a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="326a1-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="326a1-112">**Header:** None</span></span>  
<span data-ttu-id="326a1-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="326a1-113">**Library:** None</span></span>  
<span data-ttu-id="326a1-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="326a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="326a1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="326a1-115">See also</span></span>

- [<span data-ttu-id="326a1-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="326a1-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="326a1-117">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="326a1-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)