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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175614"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="61079-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="61079-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="61079-103">Obsahuje hodnoty, které popisují typ souboru mapování, která je vrácena z volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="61079-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61079-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61079-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="61079-105">Členové</span><span class="sxs-lookup"><span data-stu-id="61079-105">Members</span></span>  
  
|<span data-ttu-id="61079-106">Člen</span><span class="sxs-lookup"><span data-stu-id="61079-106">Member</span></span>|<span data-ttu-id="61079-107">Popis</span><span class="sxs-lookup"><span data-stu-id="61079-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="61079-108">Soubor je mapován jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="61079-108">The file is mapped as a data file.</span></span> <span data-ttu-id="61079-109">To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.</span><span class="sxs-lookup"><span data-stu-id="61079-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="61079-110">Soubor je mapován ke spuštění pomocí `LoadLibrary` funkce nebo `CreateFileMapping` pracovat `SEC_IMAGE` příznak.</span><span class="sxs-lookup"><span data-stu-id="61079-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61079-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61079-111">Requirements</span></span>  
 <span data-ttu-id="61079-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61079-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61079-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="61079-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="61079-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="61079-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61079-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61079-115">See also</span></span>

- [<span data-ttu-id="61079-116">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="61079-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="61079-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="61079-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
