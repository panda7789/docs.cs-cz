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
ms.openlocfilehash: bb8fba433c5f7ef9701caf61971841672f46b425
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742033"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="ca549-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="ca549-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="ca549-103">Předávání typů pro vnořený typ se přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca549-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca549-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ca549-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca549-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ca549-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="ca549-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ca549-107">ID tokenu nebo sestavení souboru, který definuje typ souboru.</span><span class="sxs-lookup"><span data-stu-id="ca549-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ca549-108">Pro typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="ca549-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="ca549-109">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="ca549-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ca549-110">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="ca549-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ca549-111">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ca549-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="ca549-112">Přijme token typu exportu.</span><span class="sxs-lookup"><span data-stu-id="ca549-112">Receives token of export type.</span></span> <span data-ttu-id="ca549-113">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="ca549-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca549-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ca549-114">Return Value</span></span>  
 <span data-ttu-id="ca549-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="ca549-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca549-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca549-116">Requirements</span></span>  
 <span data-ttu-id="ca549-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ca549-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca549-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca549-118">See also</span></span>

- [<span data-ttu-id="ca549-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca549-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ca549-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca549-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ca549-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ca549-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
