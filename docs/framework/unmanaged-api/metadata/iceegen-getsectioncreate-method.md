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
ms.openlocfilehash: 2c3c3a0168216902e5982b7d0193e72acc2bdf47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448092"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="c1202-102">ICeeGen::GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="c1202-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="c1202-103">Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.</span><span class="sxs-lookup"><span data-stu-id="c1202-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="c1202-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="c1202-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1202-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1202-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1202-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1202-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c1202-107">pro Ukazatel na řetězec, který určuje název oddílu, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c1202-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="c1202-108">pro Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="c1202-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="c1202-109">mimo Ukazatel na nově vytvořený oddíl kódu.</span><span class="sxs-lookup"><span data-stu-id="c1202-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1202-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1202-110">Remarks</span></span>  
 <span data-ttu-id="c1202-111">Vyvolejte `GetSectionCreate` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="c1202-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1202-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1202-112">Requirements</span></span>  
 <span data-ttu-id="c1202-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1202-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1202-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1202-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1202-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c1202-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1202-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1202-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1202-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1202-117">See also</span></span>

- [<span data-ttu-id="c1202-118">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1202-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
