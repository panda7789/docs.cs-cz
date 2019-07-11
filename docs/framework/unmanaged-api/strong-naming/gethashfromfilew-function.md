---
title: GetHashFromFileW – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771891"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="66198-102">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="66198-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="66198-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="66198-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="66198-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="66198-104">This function has been deprecated.</span></span> <span data-ttu-id="66198-105">Použití [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="66198-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66198-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66198-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="66198-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="66198-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="66198-108">[in] Kódování Unicode název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="66198-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="66198-109">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="66198-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="66198-110">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="66198-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="66198-111">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="66198-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="66198-112">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="66198-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="66198-113">[in] Maximální velikost vyrovnávací paměti, na které odkazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="66198-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="66198-114">[out] Velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="66198-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66198-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66198-115">Remarks</span></span>  
 <span data-ttu-id="66198-116">Tato funkce je stejná jako [gethashfromfile –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), s tím rozdílem, že specifikace názvu souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="66198-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66198-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66198-117">Requirements</span></span>  
 <span data-ttu-id="66198-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66198-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66198-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="66198-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="66198-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66198-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66198-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66198-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66198-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66198-122">See also</span></span>

- [<span data-ttu-id="66198-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="66198-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="66198-124">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="66198-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="66198-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66198-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
