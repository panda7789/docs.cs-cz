---
title: "EmbedResource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98dbd32452184bf4f832bd66ffebb0fcf3d5bb0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="ff314-102">EmbedResource – metoda</span><span class="sxs-lookup"><span data-stu-id="ff314-102">EmbedResource Method</span></span>
<span data-ttu-id="ff314-103">Deklaruje vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="ff314-103">Declares an embedded resource.</span></span> <span data-ttu-id="ff314-104">Tato metoda není ve skutečnosti vložit prostředek.</span><span class="sxs-lookup"><span data-stu-id="ff314-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff314-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff314-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff314-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff314-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ff314-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff314-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ff314-108">Soubor ID souboru, který obsahuje prostředek token nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff314-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="ff314-109">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="ff314-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ff314-110">Posun prostředku z RVA.</span><span class="sxs-lookup"><span data-stu-id="ff314-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ff314-111">Usnadnění flags – například `mrPublic` a `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="ff314-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="ff314-112">Může být předány tyto příznaky [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ff314-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff314-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff314-113">Return Value</span></span>  
 <span data-ttu-id="ff314-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ff314-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff314-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff314-115">Requirements</span></span>  
 <span data-ttu-id="ff314-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="ff314-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff314-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff314-117">See Also</span></span>  
 [<span data-ttu-id="ff314-118">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff314-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ff314-119">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff314-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ff314-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ff314-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
