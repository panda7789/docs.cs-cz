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
ms.openlocfilehash: a3056836d289383161f9fa538c3c6349f88b6ba6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905733"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="db24a-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="db24a-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="db24a-103">Obsahuje hodnoty, které popisují typ souboru mapování, která je vrácena z volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="db24a-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db24a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db24a-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="db24a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="db24a-105">Members</span></span>  
  
|<span data-ttu-id="db24a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="db24a-106">Member</span></span>|<span data-ttu-id="db24a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="db24a-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="db24a-108">Soubor je mapován jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="db24a-108">The file is mapped as a data file.</span></span> <span data-ttu-id="db24a-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="db24a-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="db24a-110">Soubor je mapován ke spuštění pomocí `LoadLibrary` funkce nebo `CreateFileMapping` pracovat `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="db24a-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db24a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db24a-111">Requirements</span></span>  
 <span data-ttu-id="db24a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db24a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db24a-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="db24a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="db24a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db24a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db24a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db24a-115">See also</span></span>

- [<span data-ttu-id="db24a-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="db24a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="db24a-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="db24a-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
