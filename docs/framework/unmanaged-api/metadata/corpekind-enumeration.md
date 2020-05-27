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
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007556"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="9cc15-102">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="9cc15-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="9cc15-103">Obsahuje hodnoty, které popisují přenositelný spustitelný soubor (PE), vrácený voláním metody [IMetaDataImport2:: GetPEKind –](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="9cc15-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cc15-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9cc15-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9cc15-105">Members</span></span>  
  
|<span data-ttu-id="9cc15-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9cc15-106">Member</span></span>|<span data-ttu-id="9cc15-107">Description</span><span class="sxs-lookup"><span data-stu-id="9cc15-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="9cc15-108">Označuje, že se nejedná o soubor PE.</span><span class="sxs-lookup"><span data-stu-id="9cc15-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="9cc15-109">Označuje, že tento soubor PE obsahuje pouze spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9cc15-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="9cc15-110">Označuje, že tento soubor PE provede volání Win32.</span><span class="sxs-lookup"><span data-stu-id="9cc15-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="9cc15-111">Označuje, že tento soubor PE běží na 64 platformě.</span><span class="sxs-lookup"><span data-stu-id="9cc15-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="9cc15-112">Označuje, že tento soubor PE je nativní kód.</span><span class="sxs-lookup"><span data-stu-id="9cc15-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="9cc15-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="9cc15-113">pe32BitPreferred</span></span>|<span data-ttu-id="9cc15-114">Označuje, že tento soubor PE je neutrální pro platformu a upřednostňuje, aby se načetla v 32 bitovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="9cc15-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cc15-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cc15-115">Remarks</span></span>  
 <span data-ttu-id="9cc15-116">Tyto hodnoty lze použít v bitových kombinacích.</span><span class="sxs-lookup"><span data-stu-id="9cc15-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cc15-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cc15-117">Requirements</span></span>  
 <span data-ttu-id="9cc15-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cc15-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cc15-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9cc15-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9cc15-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cc15-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc15-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cc15-121">See also</span></span>

- [<span data-ttu-id="9cc15-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9cc15-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
