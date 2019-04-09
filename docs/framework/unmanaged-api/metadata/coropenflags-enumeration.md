---
title: CorOpenFlags – výčet
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108511"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="fdb88-102">CorOpenFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="fdb88-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="fdb88-103">Obsahuje příznak hodnoty, které řídí chování metadata po otevření souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="fdb88-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdb88-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fdb88-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fdb88-105">Members</span></span>  
  
|<span data-ttu-id="fdb88-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fdb88-106">Member</span></span>|<span data-ttu-id="fdb88-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fdb88-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="fdb88-108">Označuje, že by soubor otevřen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fdb88-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="fdb88-109">Označuje, že soubor by měl být otevřena pro zápis.</span><span class="sxs-lookup"><span data-stu-id="fdb88-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="fdb88-110">Pokud používáte `ofWrite` příznak při otevírání souboru .winmd, je třeba také předat `ofNoTransform` příznak.</span><span class="sxs-lookup"><span data-stu-id="fdb88-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="fdb88-111">Maska pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="fdb88-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="fdb88-112">Označuje, že by soubor načíst do paměti.</span><span class="sxs-lookup"><span data-stu-id="fdb88-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="fdb88-113">Metadata musí udržovat vlastní kopii.</span><span class="sxs-lookup"><span data-stu-id="fdb88-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="fdb88-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fdb88-114">Obsolete.</span></span> <span data-ttu-id="fdb88-115">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="fdb88-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="fdb88-116">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fdb88-116">Obsolete.</span></span> <span data-ttu-id="fdb88-117">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="fdb88-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="fdb88-118">Označuje, že soubor musí být otevřen pro čtení a že volání `QueryInterface` pro [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nelze provést.</span><span class="sxs-lookup"><span data-stu-id="fdb88-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="fdb88-119">Označuje, že byla přidělena paměť pomocí volání do [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) a bude uvolněna metadata.</span><span class="sxs-lookup"><span data-stu-id="fdb88-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="fdb88-120">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fdb88-120">Obsolete.</span></span> <span data-ttu-id="fdb88-121">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="fdb88-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="fdb88-122">Označuje, že by mělo být zakázáno automatické transformace soubory .winmd.</span><span class="sxs-lookup"><span data-stu-id="fdb88-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="fdb88-123">Jinými slovy by mělo být zakázáno projekce typu modulu Windows Runtime na typ rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdb88-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="fdb88-124">Další informace najdete v tématu [Windows Runtime a CLR - pod pokličkou pomocí .NET a modulem Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="fdb88-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="fdb88-125">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="fdb88-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="fdb88-126">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="fdb88-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="fdb88-127">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="fdb88-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdb88-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdb88-128">Requirements</span></span>  
 <span data-ttu-id="fdb88-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb88-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb88-130">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fdb88-130">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="fdb88-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fdb88-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fdb88-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdb88-132">See also</span></span>

- [<span data-ttu-id="fdb88-133">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="fdb88-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
