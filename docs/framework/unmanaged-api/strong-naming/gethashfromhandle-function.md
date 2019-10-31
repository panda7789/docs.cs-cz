---
title: GetHashFromHandle – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: dc241324f5844610d7b86b7cb9668f84d4525395
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140662"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="c1da2-102">GetHashFromHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="c1da2-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="c1da2-103">Vygeneruje hodnotu hash přes obsah souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="c1da2-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c1da2-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="c1da2-104">This function has been deprecated.</span></span> <span data-ttu-id="c1da2-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromHandle –](../hosting/iclrstrongname-gethashfromhandle-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c1da2-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1da2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1da2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1da2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1da2-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="c1da2-108">pro Popisovač souboru, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="c1da2-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c1da2-109">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c1da2-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c1da2-110">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="c1da2-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c1da2-111">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="c1da2-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c1da2-112">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c1da2-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c1da2-113">mimo Velikost vrácených `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c1da2-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1da2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1da2-114">Requirements</span></span>  
 <span data-ttu-id="c1da2-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1da2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1da2-116">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c1da2-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c1da2-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1da2-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1da2-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1da2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1da2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1da2-119">See also</span></span>

- [<span data-ttu-id="c1da2-120">GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="c1da2-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="c1da2-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1da2-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
