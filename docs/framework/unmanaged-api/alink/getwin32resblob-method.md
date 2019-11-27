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
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430687"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="c81c6-102">GetWin32ResBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="c81c6-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="c81c6-103">Načte objekt BLOB prostředku Win32.</span><span class="sxs-lookup"><span data-stu-id="c81c6-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="c81c6-104">Po nastavení možností sestavení volejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c81c6-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c81c6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c81c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c81c6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c81c6-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="c81c6-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c81c6-108">Token souboru, který se používá k načtení názvu souboru, který se má použít při vytváření prostředku verze Win32</span><span class="sxs-lookup"><span data-stu-id="c81c6-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="c81c6-109">TRUE, pokud je soubor DLL, false pro EXE.</span><span class="sxs-lookup"><span data-stu-id="c81c6-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="c81c6-110">Volitelná ikona, která se má vložit do objektu BLOB prostředku</span><span class="sxs-lookup"><span data-stu-id="c81c6-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="c81c6-111">Přijímá objekt BLOB prostředku.</span><span class="sxs-lookup"><span data-stu-id="c81c6-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="c81c6-112">Přijímá velikost objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="c81c6-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c81c6-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c81c6-113">Return Value</span></span>  
 <span data-ttu-id="c81c6-114">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c81c6-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81c6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c81c6-115">Requirements</span></span>  
 <span data-ttu-id="c81c6-116">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="c81c6-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81c6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c81c6-117">See also</span></span>

- [<span data-ttu-id="c81c6-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c81c6-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c81c6-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c81c6-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c81c6-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c81c6-120">ALink API</span></span>](index.md)
