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
ms.openlocfilehash: 9a88adec508d80a40ec044e5011d3115e197e334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000542"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="0082d-102">GetHashFromAssemblyFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="0082d-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="0082d-103">Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="0082d-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="0082d-104">Jako řetězec s kódováním Unicode musí být zadána cesta k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0082d-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="0082d-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0082d-105">This function has been deprecated.</span></span> <span data-ttu-id="0082d-106">Použití [iclrstrongname::gethashfromassemblyfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="0082d-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0082d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0082d-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0082d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="0082d-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0082d-109">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="0082d-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="0082d-110">Tento parametr musí být řetězec s kódováním Unicode.</span><span class="sxs-lookup"><span data-stu-id="0082d-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0082d-111">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="0082d-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="0082d-112">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="0082d-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0082d-113">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0082d-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0082d-114">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0082d-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0082d-115">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0082d-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0082d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0082d-116">Requirements</span></span>  
 <span data-ttu-id="0082d-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0082d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0082d-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0082d-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0082d-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0082d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0082d-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0082d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0082d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0082d-121">See also</span></span>

- [<span data-ttu-id="0082d-122">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="0082d-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="0082d-123">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0082d-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="0082d-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0082d-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
