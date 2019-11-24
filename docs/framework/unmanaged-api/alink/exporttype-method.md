---
title: ExportType – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438566"
---
# <a name="exporttype-method"></a><span data-ttu-id="6d193-102">ExportType – metoda</span><span class="sxs-lookup"><span data-stu-id="6d193-102">ExportType Method</span></span>
<span data-ttu-id="6d193-103">Specifies that a type is exportable.</span><span class="sxs-lookup"><span data-stu-id="6d193-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d193-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d193-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d193-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d193-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6d193-106">ID of the assembly to export from.</span><span class="sxs-lookup"><span data-stu-id="6d193-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6d193-107">File token or assembly ID of file that defines the exportable type.</span><span class="sxs-lookup"><span data-stu-id="6d193-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="6d193-108">Token of type to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="6d193-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="6d193-109">Fully qualified type name to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="6d193-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6d193-110">`ComType` flags such as `tdPublic` or `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="6d193-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="6d193-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="6d193-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="6d193-112">Receives token for exported type.</span><span class="sxs-lookup"><span data-stu-id="6d193-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d193-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6d193-113">Return Value</span></span>  
 <span data-ttu-id="6d193-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="6d193-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d193-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d193-115">Requirements</span></span>  
 <span data-ttu-id="6d193-116">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="6d193-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d193-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d193-117">See also</span></span>

- [<span data-ttu-id="6d193-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d193-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6d193-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d193-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6d193-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="6d193-120">ALink API</span></span>](index.md)
