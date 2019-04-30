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
ms.openlocfilehash: 5bdf9fb50fe06141df6f3818c784588b9e2138af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789919"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="3c98b-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="3c98b-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="3c98b-103">Předávání typů přidá do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c98b-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c98b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c98b-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c98b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c98b-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="3c98b-106">Odkaz na sestavení, na který odkazuje předávání typů.</span><span class="sxs-lookup"><span data-stu-id="3c98b-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="3c98b-107">Plně kvalifikovaný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="3c98b-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3c98b-108">`ComType` označí jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="3c98b-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="3c98b-109">Tato hodnota může být předán [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c98b-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="3c98b-110">Přijme token exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="3c98b-110">Receives the token of the exported type.</span></span> <span data-ttu-id="3c98b-111">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="3c98b-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c98b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3c98b-112">Return Value</span></span>  
 <span data-ttu-id="3c98b-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="3c98b-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c98b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c98b-114">Requirements</span></span>  
 <span data-ttu-id="3c98b-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="3c98b-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c98b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c98b-116">See also</span></span>

- [<span data-ttu-id="3c98b-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c98b-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3c98b-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c98b-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3c98b-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="3c98b-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
