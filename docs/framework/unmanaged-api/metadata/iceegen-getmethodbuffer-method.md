---
title: ICeeGen::GetMethodBuffer – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a093b18f72cc99c53951b3dc588ce0cff3c7fefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442605"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="ff875-102">ICeeGen::GetMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="ff875-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="ff875-103">Získá odpovídající velikost vyrovnávací paměti pro metodu na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="ff875-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="ff875-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="ff875-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff875-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff875-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff875-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff875-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="ff875-107">[v] Relativní virtuální adresa metody, pro které chcete vrátit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ff875-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="ff875-108">[out] Ukazatel na vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ff875-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff875-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff875-109">Requirements</span></span>  
 <span data-ttu-id="ff875-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff875-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff875-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff875-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff875-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff875-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff875-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff875-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff875-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff875-114">See Also</span></span>  
 [<span data-ttu-id="ff875-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff875-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
