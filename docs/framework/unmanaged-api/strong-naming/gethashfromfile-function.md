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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176978"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="e7329-102">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="e7329-102">GetHashFromFile Function</span></span>
<span data-ttu-id="e7329-103">Generuje hash nad obsahem zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="e7329-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="e7329-104">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e7329-104">This function has been deprecated.</span></span> <span data-ttu-id="e7329-105">Místo toho použijte metodu [ICLRStrongName::GetHashFromFile.](../hosting/iclrstrongname-gethashfromfile-method.md)</span><span class="sxs-lookup"><span data-stu-id="e7329-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7329-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7329-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7329-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7329-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e7329-108">[v] Název souboru hash.</span><span class="sxs-lookup"><span data-stu-id="e7329-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e7329-109">[dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="e7329-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e7329-110">Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="e7329-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e7329-111">Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="e7329-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e7329-112">[out] Bajtový pole obsahující vygenerovaný hash.</span><span class="sxs-lookup"><span data-stu-id="e7329-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e7329-113">[v] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="e7329-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e7329-114">[out] Velikost vráceného bajtu v bajtech `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e7329-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7329-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7329-115">Remarks</span></span>  
 <span data-ttu-id="e7329-116">Tato funkce je stejná jako [GetHashFromFileW](gethashfromfilew-function.md), s tím rozdílem, že specifikace názvu souboru je ANSI místo Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7329-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7329-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7329-117">Requirements</span></span>  
 <span data-ttu-id="e7329-118">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7329-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7329-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e7329-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e7329-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7329-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7329-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7329-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7329-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7329-122">See also</span></span>

- [<span data-ttu-id="e7329-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="e7329-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="e7329-124">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="e7329-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="e7329-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7329-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
