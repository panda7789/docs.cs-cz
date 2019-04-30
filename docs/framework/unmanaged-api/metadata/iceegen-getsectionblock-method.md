---
title: ICeeGen::GetSectionBlock – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e600f29a9036bb28031bd7854bc8cbb34c4566a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905486"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="9fb2c-102">ICeeGen::GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="9fb2c-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="9fb2c-103">Získá blok části základu kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="9fb2c-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb2c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fb2c-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9fb2c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fb2c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="9fb2c-107">[in] Části, ze kterého se má načíst blok základu kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="9fb2c-108">[in] Délka bloku, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="9fb2c-109">[in] Byte, vzhledem k začátku části, pomocí kterého se má zarovnání prvního bajtu bloku.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="9fb2c-110">Toto je umístění bloku v rámci oddílu.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="9fb2c-111">[out] Ukazatel na umístění, která bude přijímat adresy načtený bloku.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fb2c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fb2c-112">Remarks</span></span>  
 <span data-ttu-id="9fb2c-113">Volání `GetSectionBlock` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="9fb2c-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb2c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fb2c-114">Requirements</span></span>  
 <span data-ttu-id="9fb2c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb2c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb2c-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fb2c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fb2c-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fb2c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fb2c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb2c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb2c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fb2c-119">See also</span></span>

- [<span data-ttu-id="9fb2c-120">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fb2c-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
