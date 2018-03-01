---
title: "ExportTypeForwarder – metoda"
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
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="ccb54-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="ccb54-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="ccb54-103">Předávání typů přidá do tabulky typu zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ccb54-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccb54-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccb54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccb54-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="ccb54-106">Odkaz na sestavení, na který odkazuje typ předávání.</span><span class="sxs-lookup"><span data-stu-id="ccb54-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ccb54-107">Úplný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="ccb54-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ccb54-108">`ComType`Flags – například `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ccb54-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="ccb54-109">Tato hodnota může být předaný [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ccb54-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="ccb54-110">Přijme token exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="ccb54-110">Receives the token of the exported type.</span></span> <span data-ttu-id="ccb54-111">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="ccb54-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccb54-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ccb54-112">Return Value</span></span>  
 <span data-ttu-id="ccb54-113">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ccb54-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb54-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccb54-114">Requirements</span></span>  
 <span data-ttu-id="ccb54-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ccb54-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb54-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb54-116">See Also</span></span>  
 [<span data-ttu-id="ccb54-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccb54-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ccb54-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccb54-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ccb54-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ccb54-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
