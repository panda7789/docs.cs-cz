---
title: ICeeGen::GetSectionCreate – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de3a9c152f3074339dba330b7827cf795a7e537
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745973"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="534c3-102">ICeeGen::GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="534c3-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="534c3-103">Generuje a získá oddíl kódu pomocí zadaného názvu a hodnoty příznaku.</span><span class="sxs-lookup"><span data-stu-id="534c3-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="534c3-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="534c3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="534c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="534c3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="534c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="534c3-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="534c3-107">[in] Ukazatel na řetězec určující název oddílu, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="534c3-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="534c3-108">[in] Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="534c3-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="534c3-109">[out] Ukazatel na nově vytvořený kód oddílu.</span><span class="sxs-lookup"><span data-stu-id="534c3-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="534c3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="534c3-110">Remarks</span></span>  
 <span data-ttu-id="534c3-111">Volání `GetSectionCreate` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="534c3-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="534c3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="534c3-112">Requirements</span></span>  
 <span data-ttu-id="534c3-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="534c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="534c3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="534c3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="534c3-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="534c3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="534c3-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="534c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534c3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="534c3-117">See also</span></span>

- [<span data-ttu-id="534c3-118">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="534c3-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
