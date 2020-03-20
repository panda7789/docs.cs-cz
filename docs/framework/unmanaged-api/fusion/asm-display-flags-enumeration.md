---
title: ASM_DISPLAY_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
ms.openlocfilehash: ebaab57b647250823443b48d9e45921036372d5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176601"
---
# <a name="asm_display_flags-enumeration"></a><span data-ttu-id="9dc21-102">ASM_DISPLAY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="9dc21-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="9dc21-103">Označuje verzi, sestavení, jazykovou verzi, podpis a tak dále, sestavení, jehož zobrazovaný název bude načten metodou [IAssemblyName::GetDisplayName.](iassemblyname-getdisplayname-method.md)</span><span class="sxs-lookup"><span data-stu-id="9dc21-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc21-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =
                      ASM_DISPLAYF_VERSION           |
                      ASM_DISPLAYF_CULTURE           |
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |
                      ASM_DISPLAYF_RETARGET          |
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="9dc21-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9dc21-105">Remarks</span></span>  
 <span data-ttu-id="9dc21-106">`ASM_DISPLAYF_FULL`odráží všechny změny provedené ve verzi objektu [IAssemblyName.](iassemblyname-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9dc21-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](iassemblyname-interface.md) object.</span></span> <span data-ttu-id="9dc21-107">Nepředpokládejte, že vrácená hodnota je neměnná.</span><span class="sxs-lookup"><span data-stu-id="9dc21-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc21-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dc21-108">Requirements</span></span>  
 <span data-ttu-id="9dc21-109">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc21-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc21-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9dc21-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9dc21-111">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9dc21-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc21-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc21-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc21-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dc21-113">See also</span></span>

- [<span data-ttu-id="9dc21-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dc21-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="9dc21-115">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="9dc21-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
