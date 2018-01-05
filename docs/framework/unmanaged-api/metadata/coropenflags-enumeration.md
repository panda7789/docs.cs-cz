---
title: "CorOpenFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39645de71913baeaa39524e1cae081de9cac3442
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="2661d-102">CorOpenFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="2661d-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="2661d-103">Obsahuje příznak hodnoty, které řídí chování metadat při otevírání souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="2661d-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2661d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2661d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2661d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2661d-105">Members</span></span>  
  
|<span data-ttu-id="2661d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2661d-106">Member</span></span>|<span data-ttu-id="2661d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2661d-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="2661d-108">Označuje, že soubor musí být otevřen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2661d-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="2661d-109">Označuje, že soubor musí být otevřen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="2661d-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="2661d-110">Pokud používáte `ofWrite` příznak při otevření souboru .winmd, by také předáte `ofNoTransform` příznak.</span><span class="sxs-lookup"><span data-stu-id="2661d-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="2661d-111">Maska pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="2661d-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="2661d-112">Označuje, že byste si měli přečíst soubor do paměti.</span><span class="sxs-lookup"><span data-stu-id="2661d-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="2661d-113">Metadata musí udržovat svůj vlastní kopie.</span><span class="sxs-lookup"><span data-stu-id="2661d-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="2661d-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2661d-114">Obsolete.</span></span> <span data-ttu-id="2661d-115">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2661d-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="2661d-116">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2661d-116">Obsolete.</span></span> <span data-ttu-id="2661d-117">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2661d-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="2661d-118">Označuje, že soubor musí být otevřen pro čtení a že volání `QueryInterface` pro [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nelze provést.</span><span class="sxs-lookup"><span data-stu-id="2661d-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="2661d-119">Označuje, že je paměť byl přidělen s použitím volání [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) a využívalo metadata.</span><span class="sxs-lookup"><span data-stu-id="2661d-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="2661d-120">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2661d-120">Obsolete.</span></span> <span data-ttu-id="2661d-121">Tento příznak se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2661d-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="2661d-122">Označuje, že by mělo být zakázáno automatické transformace .winmd souborů.</span><span class="sxs-lookup"><span data-stu-id="2661d-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="2661d-123">Jinými slovy by mělo být zakázáno projekce typu na typ rozhraní .NET Framework prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="2661d-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="2661d-124">Další informace najdete v tématu [pod kapotou s .NET a prostředí Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="2661d-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="2661d-125">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="2661d-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="2661d-126">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="2661d-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="2661d-127">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="2661d-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2661d-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2661d-128">Requirements</span></span>  
 <span data-ttu-id="2661d-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2661d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2661d-130">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2661d-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2661d-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2661d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2661d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2661d-132">See Also</span></span>  
 [<span data-ttu-id="2661d-133">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="2661d-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
