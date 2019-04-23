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
ms.openlocfilehash: 70d78942d4db2fea2cc1ccbcc5ddb20d743e9fdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093667"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="f20b0-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="f20b0-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="f20b0-103">Získá řetězec uložen na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="f20b0-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="f20b0-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="f20b0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f20b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f20b0-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f20b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f20b0-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="f20b0-107">[in] Relativní virtuální adresa řetězec, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="f20b0-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="f20b0-108">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="f20b0-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f20b0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f20b0-109">Requirements</span></span>  
 <span data-ttu-id="f20b0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f20b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f20b0-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f20b0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f20b0-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f20b0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f20b0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f20b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20b0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f20b0-114">See also</span></span>

- [<span data-ttu-id="f20b0-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f20b0-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
