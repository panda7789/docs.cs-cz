---
title: GetHashFromAssemblyFile – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f984d44d0a8acb85562a58653dfd2882053a0ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799285"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="1559e-102">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="1559e-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="1559e-103">Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="1559e-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="1559e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1559e-104">This function has been deprecated.</span></span> <span data-ttu-id="1559e-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromAssemblyFile –](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1559e-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1559e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1559e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1559e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1559e-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="1559e-108">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="1559e-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1559e-109">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="1559e-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1559e-110">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="1559e-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1559e-111">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="1559e-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1559e-112">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1559e-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1559e-113">mimo Vrácená velikost (v bajtech `pbHash`).</span><span class="sxs-lookup"><span data-stu-id="1559e-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1559e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1559e-114">Requirements</span></span>  
 <span data-ttu-id="1559e-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1559e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1559e-116">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="1559e-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1559e-117">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1559e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1559e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1559e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1559e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1559e-119">See also</span></span>

- [<span data-ttu-id="1559e-120">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="1559e-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="1559e-121">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="1559e-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="1559e-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1559e-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
