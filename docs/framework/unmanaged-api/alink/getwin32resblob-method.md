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
ms.openlocfilehash: f40b99c0a81bf0f2b622c7d23157dbb5736df1ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403289"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="6b03d-102">GetWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="6b03d-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="6b03d-103">Načte objekt blob Win32 prostředků.</span><span class="sxs-lookup"><span data-stu-id="6b03d-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="6b03d-104">Tuto metodu volejte po nastavení možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b03d-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b03d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b03d-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6b03d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b03d-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6b03d-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="6b03d-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6b03d-108">Používá se k načtení název souboru, který se má použít při vytváření prostředků Win32 verze token souboru</span><span class="sxs-lookup"><span data-stu-id="6b03d-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="6b03d-109">Hodnota TRUE, pokud je soubor knihovny DLL, false pro EXE.</span><span class="sxs-lookup"><span data-stu-id="6b03d-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="6b03d-110">Volitelné ikony pro vložení do objektu blob prostředků.</span><span class="sxs-lookup"><span data-stu-id="6b03d-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="6b03d-111">Získá objekt blob prostředků.</span><span class="sxs-lookup"><span data-stu-id="6b03d-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="6b03d-112">Obdrží velikost objektu blob.</span><span class="sxs-lookup"><span data-stu-id="6b03d-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b03d-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b03d-113">Return Value</span></span>  
 <span data-ttu-id="6b03d-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6b03d-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b03d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b03d-115">Requirements</span></span>  
 <span data-ttu-id="6b03d-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="6b03d-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b03d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b03d-117">See Also</span></span>  
 [<span data-ttu-id="6b03d-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b03d-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6b03d-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b03d-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6b03d-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="6b03d-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
