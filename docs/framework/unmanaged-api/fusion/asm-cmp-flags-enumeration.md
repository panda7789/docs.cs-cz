---
title: ASM_CMP_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
ms.openlocfilehash: aae122b6cf94e1205671dc7bbc0231c7d265b932
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109317"
---
# <a name="asm_cmp_flags-enumeration"></a><span data-ttu-id="87d65-102">ASM_CMP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="87d65-102">ASM_CMP_FLAGS Enumeration</span></span>
<span data-ttu-id="87d65-103">Označuje verzi, sestavení, jazykovou verzi, signaturu a tak dále, ze dvou sestavení, která mají být porovnány metodou [IAssemblyName:: EQUAL](iassemblyname-isequal-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87d65-103">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87d65-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =   
                 ASM_CMPF_MAJOR_VERSION |   
                 ASM_CMPF_MINOR_VERSION |   
                 ASM_CMPF_BUILD_NUMBER  |   
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_VERSION          |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a><span data-ttu-id="87d65-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87d65-105">Requirements</span></span>  
 <span data-ttu-id="87d65-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d65-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d65-107">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="87d65-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="87d65-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87d65-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87d65-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d65-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d65-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87d65-110">See also</span></span>

- [<span data-ttu-id="87d65-111">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87d65-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="87d65-112">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="87d65-112">Fusion Enumerations</span></span>](fusion-enumerations.md)
