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
ms.openlocfilehash: fd96b5acb22f63b6e06c981119186680d6593a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799198"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="a00df-102">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="a00df-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="a00df-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="a00df-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="a00df-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a00df-104">This function has been deprecated.</span></span> <span data-ttu-id="a00df-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromFileW –](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a00df-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00df-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a00df-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a00df-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a00df-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a00df-108">pro Název Unicode souboru, na který se má vypočítat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="a00df-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a00df-109">[in, out] Algoritmus, který má být použit při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="a00df-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="a00df-110">Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="a00df-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="a00df-111">Pokud `piHashAlg` je nastavená na 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="a00df-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a00df-112">mimo Bajtové pole obsahující vygenerovanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="a00df-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a00df-113">pro Maximální velikost vyrovnávací paměti, na `pbHash`kterou ukazuje.</span><span class="sxs-lookup"><span data-stu-id="a00df-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a00df-114">mimo Velikost v bajtech `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a00df-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a00df-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a00df-115">Remarks</span></span>  
 <span data-ttu-id="a00df-116">Tato funkce je stejná jako [GetHashFromFile –](gethashfromfile-function.md)s tím rozdílem, že specifikace názvu souboru je Unicode namísto ANSI.</span><span class="sxs-lookup"><span data-stu-id="a00df-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a00df-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a00df-117">Requirements</span></span>  
 <span data-ttu-id="a00df-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a00df-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00df-119">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a00df-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a00df-120">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a00df-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a00df-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00df-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00df-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a00df-122">See also</span></span>

- [<span data-ttu-id="a00df-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="a00df-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="a00df-124">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a00df-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="a00df-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a00df-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
