---
title: ExportTypeForwarder – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03949fb52d23e3b0f107f9f1d5208208369c3960
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574610"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="6ebe4-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="6ebe4-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="6ebe4-103">Předávání typů přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebe4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ebe4-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ebe4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ebe4-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="6ebe4-106">Odkaz na sestavení, na který odkazuje předávání typů.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="6ebe4-107">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6ebe4-108">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="6ebe4-109">Tato hodnota může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="6ebe4-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="6ebe4-110">Přijme token exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-110">Receives the token of the exported type.</span></span> <span data-ttu-id="6ebe4-111">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ebe4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ebe4-112">Return Value</span></span>  
 <span data-ttu-id="6ebe4-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="6ebe4-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ebe4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ebe4-114">Requirements</span></span>  
 <span data-ttu-id="6ebe4-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="6ebe4-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebe4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ebe4-116">See also</span></span>
- [<span data-ttu-id="6ebe4-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebe4-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6ebe4-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebe4-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6ebe4-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="6ebe4-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
