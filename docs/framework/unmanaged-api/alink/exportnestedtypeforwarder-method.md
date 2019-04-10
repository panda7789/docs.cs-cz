---
title: ExportNestedTypeForwarder – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 050ed0bbd4da38bede5a56ff95d0243f5f3cf1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220081"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="92140-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="92140-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="92140-103">Předávání typů pro vnořený typ se přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="92140-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92140-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92140-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="92140-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92140-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="92140-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="92140-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="92140-107">ID tokenu nebo sestavení souboru, který definuje typ souboru.</span><span class="sxs-lookup"><span data-stu-id="92140-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="92140-108">Pro typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="92140-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="92140-109">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="92140-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="92140-110">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="92140-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="92140-111">označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="92140-111">flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="92140-112">Přijme token typu exportu.</span><span class="sxs-lookup"><span data-stu-id="92140-112">Receives token of export type.</span></span> <span data-ttu-id="92140-113">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="92140-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92140-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92140-114">Return Value</span></span>  
 <span data-ttu-id="92140-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="92140-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92140-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92140-116">Requirements</span></span>  
 <span data-ttu-id="92140-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="92140-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92140-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92140-118">See also</span></span>

- [<span data-ttu-id="92140-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92140-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="92140-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92140-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="92140-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="92140-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
