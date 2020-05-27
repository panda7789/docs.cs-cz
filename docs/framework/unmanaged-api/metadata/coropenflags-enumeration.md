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
ms.openlocfilehash: 7318a7ea3eb1ddb047a799e58ebdfd9ce6cd76d1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007582"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="861ee-102">CorOpenFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="861ee-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="861ee-103">Obsahuje hodnoty příznaků, které řídí chování metadat při otevírání souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="861ee-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="861ee-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="861ee-105">Členové</span><span class="sxs-lookup"><span data-stu-id="861ee-105">Members</span></span>  
  
|<span data-ttu-id="861ee-106">Člen</span><span class="sxs-lookup"><span data-stu-id="861ee-106">Member</span></span>|<span data-ttu-id="861ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="861ee-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="861ee-108">Označuje, že by měl být soubor otevřen pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="861ee-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="861ee-109">Označuje, že by měl být soubor otevřen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="861ee-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="861ee-110">Pokud používáte `ofWrite` příznak při otevírání souboru WinMD, měli byste také předat `ofNoTransform` příznak.</span><span class="sxs-lookup"><span data-stu-id="861ee-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="861ee-111">Maska pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="861ee-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="861ee-112">Indikuje, že by měl být soubor čten do paměti.</span><span class="sxs-lookup"><span data-stu-id="861ee-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="861ee-113">Metadata by měla uchovávat svou vlastní kopii.</span><span class="sxs-lookup"><span data-stu-id="861ee-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="861ee-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="861ee-114">Obsolete.</span></span> <span data-ttu-id="861ee-115">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="861ee-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="861ee-116">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="861ee-116">Obsolete.</span></span> <span data-ttu-id="861ee-117">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="861ee-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="861ee-118">Označuje, že by měl být soubor otevřen pro čtení a zda `QueryInterface` nelze provést volání pro [IMetaDataEmit](imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="861ee-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="861ee-119">Indikuje, že paměť byla přidělena pomocí volání [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) a bude uvolněna metadaty.</span><span class="sxs-lookup"><span data-stu-id="861ee-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="861ee-120">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="861ee-120">Obsolete.</span></span> <span data-ttu-id="861ee-121">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="861ee-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="861ee-122">Určuje, že automatické transformace souborů. winmd by měly být zakázané.</span><span class="sxs-lookup"><span data-stu-id="861ee-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="861ee-123">Jinými slovy, je třeba zakázat projekci prostředí Windows Runtime typu pro .NET Framework typ.</span><span class="sxs-lookup"><span data-stu-id="861ee-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="861ee-124">Další informace naleznete v tématu [prostředí Windows Runtime a CLR – pod digestoří s .NET a prostředí Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span><span class="sxs-lookup"><span data-stu-id="861ee-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="861ee-125">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="861ee-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="861ee-126">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="861ee-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="861ee-127">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="861ee-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="861ee-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="861ee-128">Requirements</span></span>  
 <span data-ttu-id="861ee-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="861ee-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="861ee-130">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="861ee-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="861ee-131">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="861ee-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="861ee-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="861ee-132">See also</span></span>

- [<span data-ttu-id="861ee-133">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="861ee-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
