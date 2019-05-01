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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8f830ca7e273b65dc9ec77566a02df6c32cd464
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045536"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="c981d-102">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="c981d-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="c981d-103">Obsahuje hodnoty, které popisují soubor (PE portable executable) vrácená z volání [imetadataimport2::getpekind –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="c981d-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c981d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c981d-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="c981d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c981d-105">Members</span></span>  
  
|<span data-ttu-id="c981d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c981d-106">Member</span></span>|<span data-ttu-id="c981d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c981d-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="c981d-108">Označuje, že to není přenositelný Spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c981d-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="c981d-109">Označuje, že tento soubor PE obsahuje pouze pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c981d-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="c981d-110">Označuje, že tento soubor PE provede volání Win32.</span><span class="sxs-lookup"><span data-stu-id="c981d-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="c981d-111">Označuje, že tento soubor PE poběží na 64bitové platformě.</span><span class="sxs-lookup"><span data-stu-id="c981d-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="c981d-112">Označuje, že je tento soubor PE nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c981d-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="c981d-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="c981d-113">pe32BitPreferred</span></span>|<span data-ttu-id="c981d-114">Označuje, že tento soubor PE je nezávislá na platformě a dává přednost mají být načteny v 32bitovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="c981d-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c981d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c981d-115">Remarks</span></span>  
 <span data-ttu-id="c981d-116">Tyto hodnoty je možné v bitové kombinace.</span><span class="sxs-lookup"><span data-stu-id="c981d-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c981d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c981d-117">Requirements</span></span>  
 <span data-ttu-id="c981d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c981d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c981d-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c981d-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c981d-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c981d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c981d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c981d-121">See also</span></span>

- [<span data-ttu-id="c981d-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c981d-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
