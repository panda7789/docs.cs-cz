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
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777273"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="ba641-102">ExportNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="ba641-102">ExportNestedType Method</span></span>
<span data-ttu-id="ba641-103">Určuje vnořené typy jako exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="ba641-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="ba641-104">[Metoda ExportType](exporttype-method.md) může také exportovat vnořené typy, ale tato metoda je rychlejší.</span><span class="sxs-lookup"><span data-stu-id="ba641-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba641-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba641-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ba641-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba641-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ba641-107">ID sestavení, ze kterého se má exportovat</span><span class="sxs-lookup"><span data-stu-id="ba641-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ba641-108">Token souboru nebo sestavení souboru, které definuje typ, který se dá exportovat.</span><span class="sxs-lookup"><span data-stu-id="ba641-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ba641-109">Typ tokenu typu, který se má provést export.</span><span class="sxs-lookup"><span data-stu-id="ba641-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="ba641-110">Token nadřazeného typu</span><span class="sxs-lookup"><span data-stu-id="ba641-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ba641-111">Plně kvalifikovaný název typu, který se má exportovat</span><span class="sxs-lookup"><span data-stu-id="ba641-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ba641-112">`ComType`příznaky jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ba641-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="ba641-113">Tato hodnota může být předána [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ba641-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="ba641-114">Přijímá token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="ba641-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba641-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba641-115">Return Value</span></span>  
 <span data-ttu-id="ba641-116">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ba641-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba641-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba641-117">Requirements</span></span>  
 <span data-ttu-id="ba641-118">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="ba641-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba641-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba641-119">See also</span></span>

- [<span data-ttu-id="ba641-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba641-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ba641-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba641-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ba641-122">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ba641-122">ALink API</span></span>](index.md)
