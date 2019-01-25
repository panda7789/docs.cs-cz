---
title: GetScope – metoda1
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 782697536f5e01fa29830a64e47d960a47fe4eae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663138"
---
# <a name="getscope-method1"></a><span data-ttu-id="4869a-102">GetScope – metoda1</span><span class="sxs-lookup"><span data-stu-id="4869a-102">GetScope Method1</span></span>
<span data-ttu-id="4869a-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="4869a-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4869a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4869a-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4869a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4869a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4869a-106">Jedinečné ID sestavení, které chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="4869a-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4869a-107">Jedinečné ID souboru pro import z.</span><span class="sxs-lookup"><span data-stu-id="4869a-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4869a-108">Založený na nule oboru k importu.</span><span class="sxs-lookup"><span data-stu-id="4869a-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4869a-109">Přijímá [imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní pro obor.</span><span class="sxs-lookup"><span data-stu-id="4869a-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4869a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4869a-110">Return Value</span></span>  
 <span data-ttu-id="4869a-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="4869a-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4869a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4869a-112">Requirements</span></span>  
 <span data-ttu-id="4869a-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="4869a-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4869a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4869a-114">See also</span></span>
- [<span data-ttu-id="4869a-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4869a-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4869a-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4869a-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4869a-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="4869a-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
