---
title: "GetFileDef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a31dee6bb1af4f555211822a3b7ec108353214a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="ede37-102">GetFileDef – metoda</span><span class="sxs-lookup"><span data-stu-id="ede37-102">GetFileDef Method</span></span>
<span data-ttu-id="ede37-103">Načte skutečné FileDef tokenu používaného v metadatech (na rozdíl od token přiřadila ALink).</span><span class="sxs-lookup"><span data-stu-id="ede37-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ede37-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ede37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ede37-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ede37-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="ede37-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="ede37-107">Token souboru přidané jako načítají AddFile – metoda nebo addimport – metoda.</span><span class="sxs-lookup"><span data-stu-id="ede37-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="ede37-108">Přijme FileDef token.</span><span class="sxs-lookup"><span data-stu-id="ede37-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ede37-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ede37-109">Return Value</span></span>  
 <span data-ttu-id="ede37-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ede37-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede37-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ede37-111">Requirements</span></span>  
 <span data-ttu-id="ede37-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ede37-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede37-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ede37-113">See Also</span></span>  
 [<span data-ttu-id="ede37-114">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede37-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ede37-115">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede37-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ede37-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ede37-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
