---
title: GetWin32ResBlob – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c77ade46d2401e2499a94504808efd94f79f93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152149"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="de82b-102">GetWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="de82b-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="de82b-103">Načte objekt blob prostředků Win32.</span><span class="sxs-lookup"><span data-stu-id="de82b-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="de82b-104">Tuto metodu volejte po nastavení možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="de82b-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de82b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de82b-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="de82b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de82b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="de82b-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="de82b-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="de82b-108">Soubor tokenu se používá k načtení názvu souboru, který má být použit při vytváření prostředků Win32 verze</span><span class="sxs-lookup"><span data-stu-id="de82b-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="de82b-109">TRUE, pokud je soubor knihovny DLL, false EXE.</span><span class="sxs-lookup"><span data-stu-id="de82b-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="de82b-110">Volitelné ikony k vložení do objektu blob prostředků.</span><span class="sxs-lookup"><span data-stu-id="de82b-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="de82b-111">Přijímá objekt blob prostředků.</span><span class="sxs-lookup"><span data-stu-id="de82b-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="de82b-112">Získá velikost objektu blob.</span><span class="sxs-lookup"><span data-stu-id="de82b-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de82b-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de82b-113">Return Value</span></span>  
 <span data-ttu-id="de82b-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="de82b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de82b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de82b-115">Requirements</span></span>  
 <span data-ttu-id="de82b-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="de82b-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de82b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de82b-117">See also</span></span>

- [<span data-ttu-id="de82b-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de82b-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="de82b-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de82b-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="de82b-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="de82b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
