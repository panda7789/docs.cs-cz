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
ms.openlocfilehash: 5b28c18d55b91d6315003229295ab0e6781be183
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406302"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="9886c-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="9886c-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="9886c-103">Předávání typů přidá do tabulky typu zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="9886c-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9886c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9886c-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9886c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9886c-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="9886c-106">Odkaz na sestavení, na který odkazuje typ předávání.</span><span class="sxs-lookup"><span data-stu-id="9886c-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="9886c-107">Úplný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="9886c-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9886c-108">`ComType` Flags – například `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="9886c-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="9886c-109">Tato hodnota může být předaný [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9886c-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="9886c-110">Přijme token exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="9886c-110">Receives the token of the exported type.</span></span> <span data-ttu-id="9886c-111">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="9886c-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9886c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9886c-112">Return Value</span></span>  
 <span data-ttu-id="9886c-113">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9886c-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9886c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9886c-114">Requirements</span></span>  
 <span data-ttu-id="9886c-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="9886c-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9886c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9886c-116">See Also</span></span>  
 [<span data-ttu-id="9886c-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9886c-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9886c-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9886c-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9886c-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9886c-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
