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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220081"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="f7e54-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="f7e54-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="f7e54-103">Předávání typů pro vnořený typ se přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="f7e54-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e54-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f7e54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7e54-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f7e54-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="f7e54-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f7e54-107">ID tokenu nebo sestavení souboru, který definuje typ souboru.</span><span class="sxs-lookup"><span data-stu-id="f7e54-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="f7e54-108">Pro typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="f7e54-109">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f7e54-110">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="f7e54-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f7e54-111">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f7e54-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="f7e54-112">Přijme token typu exportu.</span><span class="sxs-lookup"><span data-stu-id="f7e54-112">Receives token of export type.</span></span> <span data-ttu-id="f7e54-113">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="f7e54-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7e54-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7e54-114">Return Value</span></span>  
 <span data-ttu-id="f7e54-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="f7e54-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e54-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7e54-116">Requirements</span></span>  
 <span data-ttu-id="f7e54-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="f7e54-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e54-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7e54-118">See also</span></span>

- [<span data-ttu-id="f7e54-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e54-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f7e54-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e54-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f7e54-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f7e54-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
