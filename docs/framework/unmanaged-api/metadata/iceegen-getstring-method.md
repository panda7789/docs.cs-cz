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
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177910"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="79ee4-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="79ee4-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="79ee4-103">Získá řetězec uložený na zadanou relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="79ee4-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="79ee4-104">Tato metoda je zastaralá a neměla by být použita.</span><span class="sxs-lookup"><span data-stu-id="79ee4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ee4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79ee4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79ee4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79ee4-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="79ee4-107">[v] Relativní virtuální adresa řetězce vrátit.</span><span class="sxs-lookup"><span data-stu-id="79ee4-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="79ee4-108">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="79ee4-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ee4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79ee4-109">Requirements</span></span>  
 <span data-ttu-id="79ee4-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79ee4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79ee4-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="79ee4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79ee4-112">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79ee4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79ee4-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79ee4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ee4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="79ee4-114">See also</span></span>

- [<span data-ttu-id="79ee4-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79ee4-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
