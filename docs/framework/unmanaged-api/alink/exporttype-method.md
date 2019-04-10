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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95ff27143453e7772b4a463fa66ca039bbb715fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226914"
---
# <a name="exporttype-method"></a><span data-ttu-id="962f0-102">ExportType – metoda</span><span class="sxs-lookup"><span data-stu-id="962f0-102">ExportType Method</span></span>
<span data-ttu-id="962f0-103">Určuje, že je typem exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="962f0-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="962f0-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="962f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="962f0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="962f0-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="962f0-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="962f0-107">Token nebo sestavení ID souboru pro soubor, který definuje typ exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="962f0-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="962f0-108">Token typu má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="962f0-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="962f0-109">Plně kvalifikovaný název typu má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="962f0-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="962f0-110">označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="962f0-110">flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="962f0-111">Tento parametr může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="962f0-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="962f0-112">Přijme token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="962f0-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="962f0-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="962f0-113">Return Value</span></span>  
 <span data-ttu-id="962f0-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="962f0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962f0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="962f0-115">Requirements</span></span>  
 <span data-ttu-id="962f0-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="962f0-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962f0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="962f0-117">See also</span></span>

- [<span data-ttu-id="962f0-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="962f0-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="962f0-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="962f0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="962f0-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="962f0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
