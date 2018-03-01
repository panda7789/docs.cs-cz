---
title: "ExportType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9cc61d0bc32545b486f4472904b17ed0b59526e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exporttype-method"></a><span data-ttu-id="9ce5a-102">ExportType – metoda</span><span class="sxs-lookup"><span data-stu-id="9ce5a-102">ExportType Method</span></span>
<span data-ttu-id="9ce5a-103">Určuje, že je typ exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ce5a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9ce5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ce5a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9ce5a-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9ce5a-107">Soubor ID souboru, který definuje typ exportovatelný token nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="9ce5a-108">Token typu, které musí být exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="9ce5a-109">Úplný název typu které musí být exportovatelný.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9ce5a-110">`ComType`Flags – například `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="9ce5a-111">Tento parametr může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9ce5a-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="9ce5a-112">Přijme token pro exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ce5a-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ce5a-113">Return Value</span></span>  
 <span data-ttu-id="9ce5a-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9ce5a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce5a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ce5a-115">Requirements</span></span>  
 <span data-ttu-id="9ce5a-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="9ce5a-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce5a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ce5a-117">See Also</span></span>  
 [<span data-ttu-id="9ce5a-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ce5a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9ce5a-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ce5a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9ce5a-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9ce5a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
