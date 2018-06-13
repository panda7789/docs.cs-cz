---
title: CorFileMapping – výčet
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c8864aa604b0483130eac5aa0d7c0640abbac99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443720"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="571f7-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="571f7-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="571f7-103">Obsahuje hodnoty, které popisují typ mapování souboru vrácená volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="571f7-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="571f7-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="571f7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="571f7-105">Members</span></span>  
  
|<span data-ttu-id="571f7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="571f7-106">Member</span></span>|<span data-ttu-id="571f7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="571f7-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="571f7-108">Soubor je namapovaný jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="571f7-108">The file is mapped as a data file.</span></span> <span data-ttu-id="571f7-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="571f7-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="571f7-110">Soubor je mapovaný pro spuštění, a to buď pomocí `LoadLibrary` funkce nebo `CreateFileMapping` fungovat s `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="571f7-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="571f7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="571f7-111">Requirements</span></span>  
 <span data-ttu-id="571f7-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="571f7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571f7-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="571f7-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="571f7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="571f7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571f7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="571f7-115">See Also</span></span>  
 [<span data-ttu-id="571f7-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="571f7-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="571f7-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="571f7-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
