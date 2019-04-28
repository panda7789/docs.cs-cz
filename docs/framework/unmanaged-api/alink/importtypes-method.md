---
title: ImportTypes – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 622e57aedf6c49e95dc2d7e40ba598361b3e6a26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753449"
---
# <a name="importtypes-method"></a><span data-ttu-id="b0ea7-102">ImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ea7-102">ImportTypes Method</span></span>
<span data-ttu-id="b0ea7-103">Inicializuje import typy z každého oboru importují prostřednictvím [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="b0ea7-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ea7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0ea7-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ea7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0ea7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b0ea7-106">ID sestavení pro import do.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b0ea7-107">ID souboru pro import z.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="b0ea7-108">Založený na nule oboru k importu.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="b0ea7-109">Získá popisovač výčtu pro typy v tomto oboru.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="b0ea7-110">Volitelně obdrží [imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="b0ea7-111">Volitelně přijímá počet typů v označeném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0ea7-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0ea7-112">Return Value</span></span>  
 <span data-ttu-id="b0ea7-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="b0ea7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ea7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0ea7-114">Requirements</span></span>  
 <span data-ttu-id="b0ea7-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="b0ea7-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ea7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0ea7-116">See also</span></span>

- [<span data-ttu-id="b0ea7-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ea7-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b0ea7-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ea7-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b0ea7-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b0ea7-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
