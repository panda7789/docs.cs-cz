---
title: ICeeGen::GetSectionDataLen – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 277e2584049fae397cf91281a65d05b0b49d9454
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448091"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="4aa89-102">ICeeGen::GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="4aa89-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="4aa89-103">Získá délku zadaného oddílu.</span><span class="sxs-lookup"><span data-stu-id="4aa89-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="4aa89-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="4aa89-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aa89-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aa89-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4aa89-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="4aa89-107">pro Datová část, jejíž délka bude načtena.</span><span class="sxs-lookup"><span data-stu-id="4aa89-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="4aa89-108">mimo Vrácená délka zadaného oddílu.</span><span class="sxs-lookup"><span data-stu-id="4aa89-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4aa89-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4aa89-109">Remarks</span></span>  
 <span data-ttu-id="4aa89-110">Vyvolejte `GetSectionDataLen` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="4aa89-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa89-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4aa89-111">Requirements</span></span>  
 <span data-ttu-id="4aa89-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aa89-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aa89-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4aa89-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4aa89-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="4aa89-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4aa89-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aa89-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa89-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4aa89-116">See also</span></span>

- [<span data-ttu-id="4aa89-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4aa89-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
