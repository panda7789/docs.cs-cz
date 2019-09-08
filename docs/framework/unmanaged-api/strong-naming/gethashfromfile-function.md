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
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799215"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="39646-102">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="39646-102">GetHashFromFile Function</span></span>
<span data-ttu-id="39646-103">Vygeneruje hodnotu hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="39646-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="39646-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="39646-104">This function has been deprecated.</span></span> <span data-ttu-id="39646-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromFile –](../hosting/iclrstrongname-gethashfromfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39646-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39646-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39646-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39646-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="39646-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="39646-108">pro Název souboru, na který se má vypočítat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="39646-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="39646-109">[in, out] Algoritmus, který má být použit při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="39646-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="39646-110">Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="39646-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="39646-111">Pokud `piHashAlg` je nastavená na 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="39646-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="39646-112">mimo Bajtové pole obsahující vygenerovanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="39646-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="39646-113">pro Maximální velikost vyrovnávací paměti, na kterou `pbHash` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="39646-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="39646-114">mimo Velikost vracené `pbHash`velikosti (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="39646-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39646-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39646-115">Remarks</span></span>  
 <span data-ttu-id="39646-116">Tato funkce je stejná jako [GetHashFromFileW –](gethashfromfilew-function.md)s tím rozdílem, že specifikace názvu souboru je ANSI namísto Unicode.</span><span class="sxs-lookup"><span data-stu-id="39646-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39646-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39646-117">Requirements</span></span>  
 <span data-ttu-id="39646-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39646-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39646-119">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="39646-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39646-120">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="39646-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39646-121">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39646-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39646-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39646-122">See also</span></span>

- [<span data-ttu-id="39646-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="39646-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="39646-124">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="39646-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="39646-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39646-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
