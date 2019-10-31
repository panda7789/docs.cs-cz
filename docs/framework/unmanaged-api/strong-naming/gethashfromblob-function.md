---
title: GetHashFromBlob – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140710"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="aa766-102">GetHashFromBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="aa766-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="aa766-103">Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="aa766-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="aa766-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="aa766-104">This function has been deprecated.</span></span> <span data-ttu-id="aa766-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromBlob –](../hosting/iclrstrongname-gethashfromblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aa766-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa766-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa766-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="aa766-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa766-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="aa766-108">pro Ukazatel na adresu bloku paměti, který má být použit jako hash.</span><span class="sxs-lookup"><span data-stu-id="aa766-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="aa766-109">pro Délka bloku paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="aa766-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="aa766-110">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="aa766-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="aa766-111">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="aa766-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="aa766-112">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="aa766-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="aa766-113">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="aa766-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="aa766-114">mimo Velikost vrácených `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="aa766-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa766-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa766-115">Requirements</span></span>

<span data-ttu-id="aa766-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa766-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="aa766-117">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="aa766-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="aa766-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa766-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="aa766-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa766-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aa766-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa766-120">See also</span></span>

- [<span data-ttu-id="aa766-121">GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="aa766-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="aa766-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa766-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
