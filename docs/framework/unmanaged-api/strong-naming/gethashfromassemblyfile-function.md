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
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140730"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="17928-102">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="17928-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="17928-103">Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="17928-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="17928-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="17928-104">This function has been deprecated.</span></span> <span data-ttu-id="17928-105">Místo toho použijte metodu [ICLRStrongName:: GetHashFromAssemblyFile –](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17928-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17928-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17928-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17928-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="17928-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="17928-108">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="17928-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="17928-109">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="17928-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="17928-110">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="17928-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="17928-111">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="17928-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="17928-112">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="17928-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="17928-113">mimo Vrácená velikost (v bajtech) `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="17928-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17928-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17928-114">Requirements</span></span>  
 <span data-ttu-id="17928-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17928-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17928-116">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="17928-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="17928-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17928-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17928-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17928-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17928-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17928-119">See also</span></span>

- [<span data-ttu-id="17928-120">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="17928-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="17928-121">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="17928-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="17928-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17928-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
