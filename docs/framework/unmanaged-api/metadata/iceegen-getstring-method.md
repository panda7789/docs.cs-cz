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
ms.openlocfilehash: e81ef33f4fb684cce29aa9afb756451b1e5db896
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426169"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="0e073-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="0e073-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="0e073-103">Získá řetězec uložený na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="0e073-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0e073-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="0e073-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e073-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e073-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e073-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e073-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="0e073-107">pro Relativní virtuální adresa řetězce, který se má vrátit</span><span class="sxs-lookup"><span data-stu-id="0e073-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="0e073-108">mimo Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="0e073-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e073-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e073-109">Requirements</span></span>  
 <span data-ttu-id="0e073-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e073-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e073-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0e073-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e073-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0e073-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e073-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e073-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e073-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e073-114">See also</span></span>

- [<span data-ttu-id="0e073-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e073-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
