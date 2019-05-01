---
title: GetHashFromFile – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049385"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="cadd6-102">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="cadd6-102">GetHashFromFile Function</span></span>
<span data-ttu-id="cadd6-103">Vygeneruje hodnotu hash nad obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="cadd6-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="cadd6-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="cadd6-104">This function has been deprecated.</span></span> <span data-ttu-id="cadd6-105">Použití [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="cadd6-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadd6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cadd6-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cadd6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cadd6-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="cadd6-108">[in] Název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="cadd6-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cadd6-109">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="cadd6-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="cadd6-110">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="cadd6-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="cadd6-111">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="cadd6-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cadd6-112">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="cadd6-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cadd6-113">[in] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="cadd6-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cadd6-114">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="cadd6-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cadd6-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cadd6-115">Remarks</span></span>  
 <span data-ttu-id="cadd6-116">Tato funkce je stejná jako [gethashfromfilew –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), s tím rozdílem, že je název specifikace souboru ANSI místo Unicode.</span><span class="sxs-lookup"><span data-stu-id="cadd6-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadd6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cadd6-117">Requirements</span></span>  
 <span data-ttu-id="cadd6-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cadd6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadd6-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cadd6-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cadd6-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cadd6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cadd6-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadd6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadd6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cadd6-122">See also</span></span>

- [<span data-ttu-id="cadd6-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="cadd6-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="cadd6-124">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="cadd6-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="cadd6-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cadd6-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
