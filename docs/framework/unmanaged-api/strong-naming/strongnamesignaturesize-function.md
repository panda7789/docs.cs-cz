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
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130877"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="47baf-102">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="47baf-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="47baf-103">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="47baf-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="47baf-104">`StrongNameSignatureSize` obvykle používá kompilátory k určení, kolik místa lze v souboru vyhradit při vytváření sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="47baf-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="47baf-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="47baf-105">This function has been deprecated.</span></span> <span data-ttu-id="47baf-106">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureSize –](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="47baf-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47baf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47baf-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="47baf-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="47baf-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="47baf-109">pro Struktura typu [PublicKeyBlob –](publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="47baf-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="47baf-110">pro Velikost `pbPublicKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="47baf-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="47baf-111">pro Počet bajtů vyžadovaných k uložení podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="47baf-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47baf-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47baf-112">Return Value</span></span>  
 <span data-ttu-id="47baf-113">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="47baf-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47baf-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47baf-114">Remarks</span></span>  
 <span data-ttu-id="47baf-115">Pokud se funkce `StrongNameSignatureSize` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="47baf-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47baf-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47baf-116">Requirements</span></span>  
 <span data-ttu-id="47baf-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47baf-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47baf-118">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="47baf-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="47baf-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47baf-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47baf-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47baf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47baf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47baf-121">See also</span></span>

- [<span data-ttu-id="47baf-122">StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="47baf-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="47baf-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47baf-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
