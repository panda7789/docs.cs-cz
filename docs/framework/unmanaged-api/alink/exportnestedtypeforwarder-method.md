---
title: "ExportNestedTypeForwarder – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41c0984e4439b89ddee2b55bbca7a098075d6bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="162b5-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="162b5-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="162b5-103">Předávání typů pro vnořené typy přidá do tabulky typu zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="162b5-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="162b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="162b5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="162b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="162b5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="162b5-106">ID sestavení, ze které chcete exportovat.</span><span class="sxs-lookup"><span data-stu-id="162b5-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="162b5-107">Soubor ID souboru, který definuje typ tokenu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="162b5-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="162b5-108">Token pro typ.</span><span class="sxs-lookup"><span data-stu-id="162b5-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="162b5-109">Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="162b5-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="162b5-110">Úplný název typu pro export.</span><span class="sxs-lookup"><span data-stu-id="162b5-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="162b5-111">`ComType`Flags – například `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="162b5-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="162b5-112">Přijme token typu export.</span><span class="sxs-lookup"><span data-stu-id="162b5-112">Receives token of export type.</span></span> <span data-ttu-id="162b5-113">To je nezbytné pouze pro generování vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="162b5-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="162b5-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="162b5-114">Return Value</span></span>  
 <span data-ttu-id="162b5-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="162b5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="162b5-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="162b5-116">Requirements</span></span>  
 <span data-ttu-id="162b5-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="162b5-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162b5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="162b5-118">See Also</span></span>  
 [<span data-ttu-id="162b5-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="162b5-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="162b5-120">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="162b5-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="162b5-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="162b5-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
