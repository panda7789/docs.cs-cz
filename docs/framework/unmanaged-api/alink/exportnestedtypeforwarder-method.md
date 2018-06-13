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
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404094"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="296b6-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="296b6-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="296b6-103">Předávání typů pro vnořené typy přidá do tabulky typu zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="296b6-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="296b6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="296b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="296b6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="296b6-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="296b6-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="296b6-107">Soubor ID souboru, který definuje typ tokenu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="296b6-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="296b6-108">Token pro typ.</span><span class="sxs-lookup"><span data-stu-id="296b6-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="296b6-109">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="296b6-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="296b6-110">Úplný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="296b6-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="296b6-111">`ComType` Flags – například `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="296b6-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="296b6-112">Přijme token typu export.</span><span class="sxs-lookup"><span data-stu-id="296b6-112">Receives token of export type.</span></span> <span data-ttu-id="296b6-113">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="296b6-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="296b6-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="296b6-114">Return Value</span></span>  
 <span data-ttu-id="296b6-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="296b6-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296b6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="296b6-116">Requirements</span></span>  
 <span data-ttu-id="296b6-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="296b6-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296b6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="296b6-118">See Also</span></span>  
 [<span data-ttu-id="296b6-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="296b6-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="296b6-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="296b6-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="296b6-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="296b6-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
