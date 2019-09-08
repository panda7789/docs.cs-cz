---
title: StrongNameGetBlob – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799099"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="ca4ed-102">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="ca4ed-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="ca4ed-103">Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="ca4ed-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-104">This function has been deprecated.</span></span> <span data-ttu-id="ca4ed-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameGetBlob –](../hosting/iclrstrongname-strongnamegetblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ca4ed-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4ed-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca4ed-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca4ed-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca4ed-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ca4ed-108">pro Platná cesta ke spustitelnému souboru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ca4ed-109">pro Vyrovnávací paměť, do které se má načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ca4ed-110">[in, out] Požadovaná maximální velikost (v bajtech `pbBlob`).</span><span class="sxs-lookup"><span data-stu-id="ca4ed-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ca4ed-111">Po vrácení se skutečnou velikostí v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca4ed-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ca4ed-112">Return Value</span></span>  
 <span data-ttu-id="ca4ed-113">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="ca4ed-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca4ed-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca4ed-114">Remarks</span></span>  
 <span data-ttu-id="ca4ed-115">Pokud se `StrongNameGetBlob` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca4ed-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca4ed-116">Requirements</span></span>  
 <span data-ttu-id="ca4ed-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4ed-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4ed-118">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ca4ed-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ca4ed-119">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca4ed-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca4ed-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4ed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4ed-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca4ed-121">See also</span></span>

- [<span data-ttu-id="ca4ed-122">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="ca4ed-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="ca4ed-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="ca4ed-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="ca4ed-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca4ed-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
