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
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140671"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="71a60-102">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="71a60-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="71a60-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="71a60-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="71a60-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="71a60-104">This function has been deprecated.</span></span> <span data-ttu-id="71a60-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromFileW –](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="71a60-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a60-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71a60-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="71a60-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="71a60-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="71a60-108">pro Název Unicode souboru, na který se má vypočítat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="71a60-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="71a60-109">[in, out] Algoritmus, který má být použit při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="71a60-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="71a60-110">Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="71a60-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="71a60-111">Je-li `piHashAlg` nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="71a60-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="71a60-112">mimo Bajtové pole obsahující vygenerovanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="71a60-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="71a60-113">pro Maximální velikost vyrovnávací paměti, na kterou ukazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="71a60-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="71a60-114">mimo Velikost `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="71a60-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71a60-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71a60-115">Remarks</span></span>  
 <span data-ttu-id="71a60-116">Tato funkce je stejná jako [GetHashFromFile –](gethashfromfile-function.md)s tím rozdílem, že specifikace názvu souboru je Unicode namísto ANSI.</span><span class="sxs-lookup"><span data-stu-id="71a60-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71a60-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71a60-117">Requirements</span></span>  
 <span data-ttu-id="71a60-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71a60-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71a60-119">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="71a60-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="71a60-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71a60-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71a60-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71a60-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a60-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71a60-122">See also</span></span>

- [<span data-ttu-id="71a60-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="71a60-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="71a60-124">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="71a60-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="71a60-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71a60-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
