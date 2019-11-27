---
title: CorPEKind – výčet
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 74670a1477546066145bd4bbf2f123a252e10b55
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436482"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="b9b47-102">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="b9b47-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="b9b47-103">Obsahuje hodnoty, které popisují přenositelný spustitelný soubor (PE), vrácený voláním metody [IMetaDataImport2:: GetPEKind –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="b9b47-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9b47-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="b9b47-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b9b47-105">Members</span></span>  
  
|<span data-ttu-id="b9b47-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b9b47-106">Member</span></span>|<span data-ttu-id="b9b47-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b9b47-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="b9b47-108">Označuje, že se nejedná o soubor PE.</span><span class="sxs-lookup"><span data-stu-id="b9b47-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="b9b47-109">Označuje, že tento soubor PE obsahuje pouze spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b9b47-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="b9b47-110">Označuje, že tento soubor PE provede volání Win32.</span><span class="sxs-lookup"><span data-stu-id="b9b47-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="b9b47-111">Označuje, že tento soubor PE běží na 64 platformě.</span><span class="sxs-lookup"><span data-stu-id="b9b47-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="b9b47-112">Označuje, že tento soubor PE je nativní kód.</span><span class="sxs-lookup"><span data-stu-id="b9b47-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="b9b47-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="b9b47-113">pe32BitPreferred</span></span>|<span data-ttu-id="b9b47-114">Označuje, že tento soubor PE je neutrální pro platformu a upřednostňuje, aby se načetla v 32 bitovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="b9b47-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b47-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9b47-115">Remarks</span></span>  
 <span data-ttu-id="b9b47-116">Tyto hodnoty lze použít v bitových kombinacích.</span><span class="sxs-lookup"><span data-stu-id="b9b47-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b47-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9b47-117">Requirements</span></span>  
 <span data-ttu-id="b9b47-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b47-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b47-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b9b47-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b9b47-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b47-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b47-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9b47-121">See also</span></span>

- [<span data-ttu-id="b9b47-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b9b47-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
