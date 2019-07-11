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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: febf952dbfd80a37017cb165aec4a6b207052d1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745941"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="283ed-102">ICeeGen::GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="283ed-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="283ed-103">Získá délku zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="283ed-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="283ed-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="283ed-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="283ed-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="283ed-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="283ed-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="283ed-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="283ed-107">[in] Datové části, jehož délka budou načítat.</span><span class="sxs-lookup"><span data-stu-id="283ed-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="283ed-108">[out] Vrácená délka zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="283ed-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="283ed-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="283ed-109">Remarks</span></span>  
 <span data-ttu-id="283ed-110">Volání `GetSectionDataLen` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="283ed-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="283ed-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="283ed-111">Requirements</span></span>  
 <span data-ttu-id="283ed-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="283ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="283ed-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="283ed-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="283ed-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="283ed-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="283ed-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="283ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283ed-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="283ed-116">See also</span></span>

- [<span data-ttu-id="283ed-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="283ed-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
