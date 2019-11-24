---
title: GetFileDef – metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 6a561205602920123176bd421ca2ef1b601166c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426048"
---
# <a name="getfiledef-method"></a><span data-ttu-id="d8526-102">GetFileDef – metoda</span><span class="sxs-lookup"><span data-stu-id="d8526-102">GetFileDef Method</span></span>
<span data-ttu-id="d8526-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span><span class="sxs-lookup"><span data-stu-id="d8526-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8526-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8526-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8526-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8526-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d8526-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="d8526-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="d8526-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span><span class="sxs-lookup"><span data-stu-id="d8526-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="d8526-108">Receives the FileDef token.</span><span class="sxs-lookup"><span data-stu-id="d8526-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8526-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8526-109">Return Value</span></span>  
 <span data-ttu-id="d8526-110">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="d8526-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8526-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8526-111">Requirements</span></span>  
 <span data-ttu-id="d8526-112">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="d8526-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8526-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8526-113">See also</span></span>

- [<span data-ttu-id="d8526-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8526-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d8526-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8526-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d8526-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="d8526-116">ALink API</span></span>](index.md)
