---
title: "SetManifestFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="feae9-102">SetManifestFile – metoda</span><span class="sxs-lookup"><span data-stu-id="feae9-102">SetManifestFile Method</span></span>
<span data-ttu-id="feae9-103">Umožňuje zadat nebo obnovit soubor manifestu, který linkeru používá při vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="feae9-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feae9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feae9-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="feae9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="feae9-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="feae9-106">Název souboru manifestu, jejichž obsah jsou vloženy do objektu blob Win32 prostředky.</span><span class="sxs-lookup"><span data-stu-id="feae9-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feae9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="feae9-107">Return Value</span></span>  
 <span data-ttu-id="feae9-108">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="feae9-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feae9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feae9-109">Remarks</span></span>  
 <span data-ttu-id="feae9-110">Toto volání před žádostí o Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="feae9-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="feae9-111">Hodnota `pszFile` parametr je název souboru manifestu, jejichž obsah čtou a umístit do Win32 prostředky s ID RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="feae9-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="feae9-112">Při volání pomocí parametr hodnotu NULL, není zaškrtnuté všechny dříve čtení manifestu.</span><span class="sxs-lookup"><span data-stu-id="feae9-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="feae9-113">To umožňuje jednu pro obnovení stav linkeru, čas inicializace.</span><span class="sxs-lookup"><span data-stu-id="feae9-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feae9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="feae9-114">Requirements</span></span>  
 <span data-ttu-id="feae9-115">Vyžaduje aLink.h</span><span class="sxs-lookup"><span data-stu-id="feae9-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feae9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="feae9-116">See Also</span></span>  
 [<span data-ttu-id="feae9-117">Ialink3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="feae9-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="feae9-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="feae9-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="feae9-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="feae9-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="feae9-120">Al.exe (Linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="feae9-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
