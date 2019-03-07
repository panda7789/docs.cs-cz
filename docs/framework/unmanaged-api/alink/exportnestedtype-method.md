---
title: ExportNestedType – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49dc456df684d6905370ee6ab8c8883449bea990
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498039"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="e5edf-102">ExportNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="e5edf-102">ExportNestedType Method</span></span>
<span data-ttu-id="e5edf-103">Určuje vnořené typy jako exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="e5edf-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="e5edf-104">[ExportType – metoda](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) můžete také exportovat vnořené typy, ale tato metoda je rychlejší.</span><span class="sxs-lookup"><span data-stu-id="e5edf-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5edf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5edf-105">Syntax</span></span>  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="e5edf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5edf-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e5edf-107">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="e5edf-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5edf-108">Token souboru nebo sestavení souboru, který definuje typ má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="e5edf-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="e5edf-109">Zadejte token typu má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="e5edf-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="e5edf-110">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="e5edf-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e5edf-111">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="e5edf-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e5edf-112">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e5edf-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e5edf-113">Tato hodnota může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5edf-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e5edf-114">Přijme token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="e5edf-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5edf-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5edf-115">Return Value</span></span>  
 <span data-ttu-id="e5edf-116">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="e5edf-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5edf-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5edf-117">Requirements</span></span>  
 <span data-ttu-id="e5edf-118">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="e5edf-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5edf-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5edf-119">See also</span></span>
- [<span data-ttu-id="e5edf-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5edf-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e5edf-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5edf-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e5edf-122">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e5edf-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
