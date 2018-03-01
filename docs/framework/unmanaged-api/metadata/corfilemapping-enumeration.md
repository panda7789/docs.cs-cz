---
title: "CorFileMapping – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5abde0d34baecf12628c9c6c99f04d6d81dd62fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="47456-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="47456-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="47456-103">Obsahuje hodnoty, které popisují typ mapování souboru vrácená volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="47456-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47456-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47456-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="47456-105">Členové</span><span class="sxs-lookup"><span data-stu-id="47456-105">Members</span></span>  
  
|<span data-ttu-id="47456-106">Člen</span><span class="sxs-lookup"><span data-stu-id="47456-106">Member</span></span>|<span data-ttu-id="47456-107">Popis</span><span class="sxs-lookup"><span data-stu-id="47456-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="47456-108">Soubor je namapovaný jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="47456-108">The file is mapped as a data file.</span></span> <span data-ttu-id="47456-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="47456-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="47456-110">Soubor je mapovaný pro spuštění, a to buď pomocí `LoadLibrary` funkce nebo `CreateFileMapping` fungovat s `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="47456-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47456-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47456-111">Requirements</span></span>  
 <span data-ttu-id="47456-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47456-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47456-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="47456-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="47456-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47456-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47456-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="47456-115">See Also</span></span>  
 [<span data-ttu-id="47456-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="47456-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="47456-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="47456-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
