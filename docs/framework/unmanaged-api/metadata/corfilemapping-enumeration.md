---
title: "CorFileMapping – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileMapping
helpviewer_keywords: CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6736f154ef6b03c0bfe34d16a419955324316273
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="c2798-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="c2798-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="c2798-103">Obsahuje hodnoty, které popisují typ mapování souboru vrácená volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c2798-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2798-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2798-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="c2798-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c2798-105">Members</span></span>  
  
|<span data-ttu-id="c2798-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c2798-106">Member</span></span>|<span data-ttu-id="c2798-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c2798-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="c2798-108">Soubor je namapovaný jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="c2798-108">The file is mapped as a data file.</span></span> <span data-ttu-id="c2798-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="c2798-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="c2798-110">Soubor je mapovaný pro spuštění, a to buď pomocí `LoadLibrary` funkce nebo `CreateFileMapping` fungovat s `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="c2798-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2798-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2798-111">Requirements</span></span>  
 <span data-ttu-id="c2798-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2798-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2798-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c2798-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c2798-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2798-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2798-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2798-115">See Also</span></span>  
 [<span data-ttu-id="c2798-116">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="c2798-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="c2798-117">Getfilemapping – metoda</span><span class="sxs-lookup"><span data-stu-id="c2798-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
