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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772048"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="d0991-102">GetHashFromAssemblyFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="d0991-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="d0991-103">Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="d0991-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="d0991-104">Jako řetězec s kódováním Unicode musí být zadána cesta k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0991-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="d0991-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="d0991-105">This function has been deprecated.</span></span> <span data-ttu-id="d0991-106">Použití [iclrstrongname::gethashfromassemblyfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="d0991-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0991-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0991-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0991-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0991-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d0991-109">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="d0991-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="d0991-110">Tento parametr musí být řetězec s kódováním Unicode.</span><span class="sxs-lookup"><span data-stu-id="d0991-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d0991-111">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d0991-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d0991-112">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="d0991-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d0991-113">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0991-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d0991-114">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d0991-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d0991-115">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d0991-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0991-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0991-116">Requirements</span></span>  
 <span data-ttu-id="d0991-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0991-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0991-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d0991-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d0991-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0991-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0991-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0991-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0991-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0991-121">See also</span></span>

- [<span data-ttu-id="d0991-122">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="d0991-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="d0991-123">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d0991-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="d0991-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0991-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
