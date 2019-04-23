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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175614"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="02ee2-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="02ee2-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="02ee2-103">Obsahuje hodnoty, které popisují typ souboru mapování, která je vrácena z volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="02ee2-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ee2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02ee2-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="02ee2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="02ee2-105">Members</span></span>  
  
|<span data-ttu-id="02ee2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="02ee2-106">Member</span></span>|<span data-ttu-id="02ee2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="02ee2-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="02ee2-108">Soubor je mapován jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="02ee2-108">The file is mapped as a data file.</span></span> <span data-ttu-id="02ee2-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="02ee2-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="02ee2-110">Soubor je mapován ke spuštění pomocí `LoadLibrary` funkce nebo `CreateFileMapping` pracovat `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="02ee2-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02ee2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02ee2-111">Requirements</span></span>  
 <span data-ttu-id="02ee2-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02ee2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ee2-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="02ee2-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="02ee2-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ee2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ee2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02ee2-115">See also</span></span>

- [<span data-ttu-id="02ee2-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="02ee2-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="02ee2-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="02ee2-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
