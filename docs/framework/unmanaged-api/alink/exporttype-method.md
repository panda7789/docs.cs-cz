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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226914"
---
# <a name="exporttype-method"></a><span data-ttu-id="3fbcd-102">ExportType – metoda</span><span class="sxs-lookup"><span data-stu-id="3fbcd-102">ExportType Method</span></span>
<span data-ttu-id="3fbcd-103">Určuje, že je typem exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fbcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fbcd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3fbcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fbcd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3fbcd-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3fbcd-107">Token nebo sestavení ID souboru pro soubor, který definuje typ exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="3fbcd-108">Token typu má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="3fbcd-109">Plně kvalifikovaný název typu má být provedeno exportovatelné.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3fbcd-110">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="3fbcd-111">Tento parametr může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3fbcd-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="3fbcd-112">Přijme token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fbcd-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3fbcd-113">Return Value</span></span>  
 <span data-ttu-id="3fbcd-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="3fbcd-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fbcd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fbcd-115">Requirements</span></span>  
 <span data-ttu-id="3fbcd-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="3fbcd-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fbcd-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fbcd-117">See also</span></span>

- [<span data-ttu-id="3fbcd-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fbcd-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3fbcd-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fbcd-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3fbcd-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="3fbcd-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
