---
title: StrongNameGetBlobFromImage – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799086"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="cc653-102">StrongNameGetBlobFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="cc653-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="cc653-103">Načte binární reprezentaci image sestavení v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="cc653-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="cc653-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="cc653-104">This function has been deprecated.</span></span> <span data-ttu-id="cc653-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameGetBlobFromImage –](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cc653-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc653-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc653-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc653-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc653-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="cc653-108">pro Adresa paměti namapovaného manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc653-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="cc653-109">pro Velikost obrázku `pbBase`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="cc653-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="cc653-110">pro Vyrovnávací paměť obsahující binární reprezentaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="cc653-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="cc653-111">[in, out] Požadovaná maximální velikost (v bajtech `pbBlob`).</span><span class="sxs-lookup"><span data-stu-id="cc653-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="cc653-112">Po vrácení se skutečnou velikostí v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="cc653-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc653-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc653-113">Return Value</span></span>  
 <span data-ttu-id="cc653-114">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="cc653-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc653-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc653-115">Remarks</span></span>  
 <span data-ttu-id="cc653-116">Pokud se `StrongNameGetBlobFromImage` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="cc653-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc653-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc653-117">Requirements</span></span>  
 <span data-ttu-id="cc653-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc653-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc653-119">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="cc653-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cc653-120">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc653-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc653-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc653-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc653-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc653-122">See also</span></span>

- [<span data-ttu-id="cc653-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="cc653-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="cc653-124">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="cc653-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="cc653-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc653-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
