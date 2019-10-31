---
title: GetHashFromAssemblyFileW – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140696"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="04e11-102">GetHashFromAssemblyFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="04e11-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="04e11-103">Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="04e11-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="04e11-104">Cesta k souboru sestavení musí být zadána jako řetězec Unicode.</span><span class="sxs-lookup"><span data-stu-id="04e11-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="04e11-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="04e11-105">This function has been deprecated.</span></span> <span data-ttu-id="04e11-106">Místo toho použijte metodu [ICLRStrongName:: gethashfromassemblyfilew –](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04e11-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e11-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e11-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e11-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="04e11-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="04e11-109">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="04e11-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="04e11-110">Tento parametr musí být řetězec Unicode.</span><span class="sxs-lookup"><span data-stu-id="04e11-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="04e11-111">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="04e11-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="04e11-112">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="04e11-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="04e11-113">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="04e11-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="04e11-114">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="04e11-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="04e11-115">mimo Vrácená velikost (v bajtech) `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="04e11-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e11-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04e11-116">Requirements</span></span>  
 <span data-ttu-id="04e11-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e11-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e11-118">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="04e11-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="04e11-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04e11-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e11-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e11-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e11-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e11-121">See also</span></span>

- [<span data-ttu-id="04e11-122">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="04e11-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="04e11-123">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="04e11-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="04e11-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04e11-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
