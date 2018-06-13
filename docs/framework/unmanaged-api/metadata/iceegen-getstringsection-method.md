---
title: ICeeGen::GetStringSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a8617c9e818ec514c912a85373c916559d89df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443034"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="ea97f-102">ICeeGen::GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="ea97f-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="ea97f-103">Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="ea97f-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="ea97f-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="ea97f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea97f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea97f-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea97f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea97f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ea97f-107">[ve out] Popisovač části kódu.</span><span class="sxs-lookup"><span data-stu-id="ea97f-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea97f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea97f-108">Requirements</span></span>  
 <span data-ttu-id="ea97f-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea97f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea97f-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea97f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea97f-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea97f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea97f-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea97f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea97f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea97f-113">See Also</span></span>  
 [<span data-ttu-id="ea97f-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea97f-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
