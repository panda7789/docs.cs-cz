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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179417"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="d1a83-102">ExportNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="d1a83-102">ExportNestedType Method</span></span>
<span data-ttu-id="d1a83-103">Určuje vnořené typy jako exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="d1a83-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="d1a83-104">[Metoda ExportType](exporttype-method.md) může také exportovat vnořené typy, ale tato metoda je rychlejší.</span><span class="sxs-lookup"><span data-stu-id="d1a83-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1a83-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d1a83-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1a83-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d1a83-107">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="d1a83-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d1a83-108">Token souboru nebo sestavení souboru, který definuje typ, který má být exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="d1a83-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="d1a83-109">Typ token typu, který má být exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="d1a83-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="d1a83-110">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="d1a83-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="d1a83-111">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="d1a83-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d1a83-112">`ComType`příznaky, `tdPublic` jako `tdNested`jsou například nebo .</span><span class="sxs-lookup"><span data-stu-id="d1a83-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="d1a83-113">Tato hodnota může být [předána metodě DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="d1a83-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="d1a83-114">Přijímá token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="d1a83-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1a83-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1a83-115">Return Value</span></span>  
 <span data-ttu-id="d1a83-116">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d1a83-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a83-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1a83-117">Requirements</span></span>  
 <span data-ttu-id="d1a83-118">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="d1a83-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a83-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1a83-119">See also</span></span>

- [<span data-ttu-id="d1a83-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1a83-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d1a83-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1a83-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d1a83-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="d1a83-122">ALink API</span></span>](index.md)
