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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007387"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="b9083-102">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="b9083-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="b9083-103">Obsahuje hodnoty, které popisují typ mapování souboru, které je vráceno voláním metody [IMetaDataInfo –:: GetFileMapping –](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9083-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9083-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9083-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="b9083-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b9083-105">Members</span></span>  
  
|<span data-ttu-id="b9083-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b9083-106">Member</span></span>|<span data-ttu-id="b9083-107">Description</span><span class="sxs-lookup"><span data-stu-id="b9083-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="b9083-108">Soubor je namapován jako datový soubor.</span><span class="sxs-lookup"><span data-stu-id="b9083-108">The file is mapped as a data file.</span></span> <span data-ttu-id="b9083-109">To znamená, že `SEC_IMAGE` Příznak nebyl předán funkci Microsoft Win32 `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="b9083-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="b9083-110">Soubor je namapován pro provedení pomocí `LoadLibrary` funkce nebo `CreateFileMapping` funkce s `SEC_IMAGE` příznakem.</span><span class="sxs-lookup"><span data-stu-id="b9083-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9083-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9083-111">Requirements</span></span>  
 <span data-ttu-id="b9083-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9083-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9083-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b9083-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b9083-114">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9083-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9083-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9083-115">See also</span></span>

- [<span data-ttu-id="b9083-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b9083-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="b9083-117">GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="b9083-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
