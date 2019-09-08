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
ms.openlocfilehash: b26f08548ac964fae2f4d64db50167add327eb2d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777366"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="fde66-102">GetWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="fde66-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="fde66-103">Načte objekt BLOB prostředku Win32.</span><span class="sxs-lookup"><span data-stu-id="fde66-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="fde66-104">Po nastavení možností sestavení volejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="fde66-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde66-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fde66-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fde66-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fde66-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fde66-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="fde66-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="fde66-108">Token souboru, který se používá k načtení názvu souboru, který se má použít při vytváření prostředku verze Win32</span><span class="sxs-lookup"><span data-stu-id="fde66-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="fde66-109">TRUE, pokud je soubor DLL, false pro EXE.</span><span class="sxs-lookup"><span data-stu-id="fde66-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="fde66-110">Volitelná ikona, která se má vložit do objektu BLOB prostředku</span><span class="sxs-lookup"><span data-stu-id="fde66-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="fde66-111">Přijímá objekt BLOB prostředku.</span><span class="sxs-lookup"><span data-stu-id="fde66-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="fde66-112">Přijímá velikost objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="fde66-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fde66-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fde66-113">Return Value</span></span>  
 <span data-ttu-id="fde66-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fde66-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde66-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fde66-115">Requirements</span></span>  
 <span data-ttu-id="fde66-116">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="fde66-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde66-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fde66-117">See also</span></span>

- [<span data-ttu-id="fde66-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fde66-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fde66-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fde66-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fde66-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="fde66-120">ALink API</span></span>](index.md)
