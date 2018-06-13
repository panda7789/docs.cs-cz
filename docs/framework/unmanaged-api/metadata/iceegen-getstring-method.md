---
title: ICeeGen::GetString – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7ac5ef95ca3705b11cfda51d7fd1aca7400abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443070"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="50c80-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="50c80-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="50c80-103">Získá řetězec uložený na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="50c80-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="50c80-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="50c80-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c80-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50c80-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50c80-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50c80-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="50c80-107">[v] Relativní virtuální adresa řetězec, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="50c80-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="50c80-108">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="50c80-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c80-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50c80-109">Requirements</span></span>  
 <span data-ttu-id="50c80-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c80-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c80-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50c80-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50c80-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50c80-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50c80-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c80-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="50c80-114">See Also</span></span>  
 [<span data-ttu-id="50c80-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50c80-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
