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
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445557"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="9dd6d-102">SetManifestFile – metoda</span><span class="sxs-lookup"><span data-stu-id="9dd6d-102">SetManifestFile Method</span></span>
<span data-ttu-id="9dd6d-103">Umožňuje určit nebo obnovit soubor manifestu, který Linker používá při vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dd6d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dd6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dd6d-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="9dd6d-106">Název souboru manifestu, jehož obsah je umístěn do objektu BLOB prostředků Win32.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dd6d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9dd6d-107">Return Value</span></span>  
 <span data-ttu-id="9dd6d-108">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dd6d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9dd6d-109">Remarks</span></span>  
 <span data-ttu-id="9dd6d-110">Před dotazem na Win32ResBlobu tento hovor zavolejte.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="9dd6d-111">Hodnota parametru `pszFile` je název souboru manifestu, jehož obsah je čten a umístěn do prostředků Win32 s ID RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="9dd6d-112">Pokud je volána pomocí parametru NULL, všechny dříve přečtené manifesty jsou vymazány.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="9dd6d-113">To umožňuje, aby se stav linkeru obnovil na čas inicializace.</span><span class="sxs-lookup"><span data-stu-id="9dd6d-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd6d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dd6d-114">Requirements</span></span>  
 <span data-ttu-id="9dd6d-115">Vyžaduje aLink. h</span><span class="sxs-lookup"><span data-stu-id="9dd6d-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd6d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dd6d-116">See also</span></span>

- [<span data-ttu-id="9dd6d-117">IALink3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dd6d-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="9dd6d-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9dd6d-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="9dd6d-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dd6d-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9dd6d-120">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="9dd6d-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
