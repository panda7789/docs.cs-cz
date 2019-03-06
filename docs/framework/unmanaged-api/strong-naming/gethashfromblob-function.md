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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352071"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="b7391-102">GetHashFromBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="b7391-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="b7391-103">Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="b7391-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="b7391-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b7391-104">This function has been deprecated.</span></span> <span data-ttu-id="b7391-105">Použití [iclrstrongname::gethashfromblob –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="b7391-105">Use the [ICLRStrongName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7391-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7391-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b7391-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7391-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="b7391-108">[in] Ukazatel na adresu blok paměti určený k hashovat.</span><span class="sxs-lookup"><span data-stu-id="b7391-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="b7391-109">[in] Délka v bajtech, bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="b7391-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="b7391-110">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="b7391-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b7391-111">Použít nulu pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b7391-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="b7391-112">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b7391-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="b7391-113">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b7391-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="b7391-114">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b7391-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7391-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7391-115">Requirements</span></span>

<span data-ttu-id="b7391-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7391-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b7391-117">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b7391-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="b7391-118">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7391-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="b7391-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7391-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b7391-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7391-120">See also</span></span>

- [<span data-ttu-id="b7391-121">GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="b7391-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="b7391-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7391-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)