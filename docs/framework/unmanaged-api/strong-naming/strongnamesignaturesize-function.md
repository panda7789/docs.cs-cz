---
title: StrongNameSignatureSize – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176887"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="c304f-102">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="c304f-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="c304f-103">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="c304f-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="c304f-104">`StrongNameSignatureSize`obvykle používá kompilátory k určení, kolik místa rezervovat v souboru při vytváření sestavení podepsané zpoždění.</span><span class="sxs-lookup"><span data-stu-id="c304f-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="c304f-105">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="c304f-105">This function has been deprecated.</span></span> <span data-ttu-id="c304f-106">Místo toho použijte metodu [ICLRStrongName::StrongNameSignatureSize.](../hosting/iclrstrongname-strongnamesignaturesize-method.md)</span><span class="sxs-lookup"><span data-stu-id="c304f-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c304f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c304f-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c304f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="c304f-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="c304f-109">[v] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) který obsahuje veřejnou část dvojice klíčů slouží ke generování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="c304f-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="c304f-110">[v] Velikost v bajtů `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c304f-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c304f-111">[v] Počet bajtů potřebných k uložení podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="c304f-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c304f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c304f-112">Return Value</span></span>  
 <span data-ttu-id="c304f-113">`true`po úspěšném dokončení; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="c304f-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c304f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c304f-114">Remarks</span></span>  
 <span data-ttu-id="c304f-115">Pokud `StrongNameSignatureSize` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="c304f-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c304f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c304f-116">Requirements</span></span>  
 <span data-ttu-id="c304f-117">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c304f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c304f-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c304f-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c304f-119">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c304f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c304f-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c304f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c304f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c304f-121">See also</span></span>

- [<span data-ttu-id="c304f-122">StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="c304f-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="c304f-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c304f-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
