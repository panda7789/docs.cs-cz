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
ms.openlocfilehash: b7b15261d825c1bd5f217c4cecd82ed36a716d0e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008258"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="2c3b0-102">ICeeGen::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="2c3b0-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="2c3b0-103">Získá řetězec uložený na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="2c3b0-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="2c3b0-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="2c3b0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c3b0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c3b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c3b0-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="2c3b0-107">pro Relativní virtuální adresa řetězce, který se má vrátit</span><span class="sxs-lookup"><span data-stu-id="2c3b0-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="2c3b0-108">mimo Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="2c3b0-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3b0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c3b0-109">Requirements</span></span>  
 <span data-ttu-id="2c3b0-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3b0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3b0-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c3b0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c3b0-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="2c3b0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3b0-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3b0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c3b0-114">See also</span></span>

- [<span data-ttu-id="2c3b0-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c3b0-115">ICeeGen Interface</span></span>](iceegen-interface.md)
