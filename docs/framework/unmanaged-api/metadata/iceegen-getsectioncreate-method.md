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
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008325"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="fc1a4-102">ICeeGen::GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="fc1a4-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="fc1a4-103">Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="fc1a4-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc1a4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc1a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc1a4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc1a4-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fc1a4-107">pro Ukazatel na řetězec, který určuje název oddílu, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="fc1a4-108">pro Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="fc1a4-109">mimo Ukazatel na nově vytvořený oddíl kódu.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc1a4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc1a4-110">Remarks</span></span>  
 <span data-ttu-id="fc1a4-111">Volejte `GetSectionCreate` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc1a4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc1a4-112">Requirements</span></span>  
 <span data-ttu-id="fc1a4-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc1a4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc1a4-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc1a4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc1a4-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="fc1a4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc1a4-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc1a4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1a4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc1a4-117">See also</span></span>

- [<span data-ttu-id="fc1a4-118">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc1a4-118">ICeeGen Interface</span></span>](iceegen-interface.md)
