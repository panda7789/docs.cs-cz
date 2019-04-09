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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01c0f9ca0299e817618d93133c0eaca9fc63788e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160313"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="2344f-102">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="2344f-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="2344f-103">Vrátí velikost položky podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2344f-103">Returns the size of the strong name signature.</span></span> `StrongNameSignatureSize` <span data-ttu-id="2344f-104">se obvykle používá kompilátory k určení, kolik místa vyhradit v souboru při vytváření sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="2344f-104">is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="2344f-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="2344f-105">This function has been deprecated.</span></span> <span data-ttu-id="2344f-106">Použití [iclrstrongname::strongnamesignaturesize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="2344f-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2344f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2344f-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="2344f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="2344f-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="2344f-109">[in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2344f-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="2344f-110">[in] Velikost v bajtech, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2344f-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="2344f-111">[in] Počet bajtů vyžadovaných k uložení podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2344f-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2344f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2344f-112">Return Value</span></span>  
 `true` <span data-ttu-id="2344f-113">Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2344f-113">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2344f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2344f-114">Remarks</span></span>  
 <span data-ttu-id="2344f-115">Pokud `StrongNameSignatureSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="2344f-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2344f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2344f-116">Requirements</span></span>  
 <span data-ttu-id="2344f-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2344f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2344f-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2344f-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2344f-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2344f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2344f-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2344f-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2344f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2344f-121">See also</span></span>

- [<span data-ttu-id="2344f-122">StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="2344f-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="2344f-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2344f-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
