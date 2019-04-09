---
title: SetManifestFile – metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072425"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="a8f1a-102">SetManifestFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a8f1a-102">SetManifestFile Method</span></span>
<span data-ttu-id="a8f1a-103">Umožňuje zadat nebo obnovit soubor manifestu, který používá propojovací program při vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8f1a-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8f1a-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="a8f1a-106">Název souboru manifestu, jejichž obsah jsou vloženy do objektu blob prostředky Win32.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f1a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8f1a-107">Return Value</span></span>  
 <span data-ttu-id="a8f1a-108">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8f1a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8f1a-109">Remarks</span></span>  
 <span data-ttu-id="a8f1a-110">Před požadující Win32ResBlob volejte to.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="a8f1a-111">Hodnota `pszFile` parametr je název souboru manifestu, jejichž obsah čtou a vložit prostředky Win32 s ID RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="a8f1a-112">Při volání s použitím parametr hodnotu NULL, se vymaže všechny dříve čtení manifestu.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="a8f1a-113">To umožňuje z nich se má obnovit stav linkeru, inicializuje.</span><span class="sxs-lookup"><span data-stu-id="a8f1a-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f1a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8f1a-114">Requirements</span></span>  
 <span data-ttu-id="a8f1a-115">Vyžaduje aLink.h</span><span class="sxs-lookup"><span data-stu-id="a8f1a-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f1a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f1a-116">See also</span></span>

- [<span data-ttu-id="a8f1a-117">IALink3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8f1a-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [<span data-ttu-id="a8f1a-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="a8f1a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
- [<span data-ttu-id="a8f1a-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8f1a-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a8f1a-120">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="a8f1a-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
