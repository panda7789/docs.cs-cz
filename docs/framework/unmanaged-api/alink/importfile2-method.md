---
title: ImportFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446980"
---
# <a name="importfile2-method"></a><span data-ttu-id="77a0b-102">ImportFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="77a0b-102">ImportFile2 Method</span></span>
<span data-ttu-id="77a0b-103">Importuje sestavení a nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="77a0b-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="77a0b-104">Tato metoda se podobá [metodě importFile –](importfile-method.md), ale funguje i v případě, že soubor, který importujete, na disku neexistuje.</span><span class="sxs-lookup"><span data-stu-id="77a0b-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a0b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77a0b-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="77a0b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="77a0b-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="77a0b-107">Název souboru, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="77a0b-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="77a0b-108">Volitelný název výstupního souboru, který lze použít k přejmenování souboru, protože je propojen do sestavení.</span><span class="sxs-lookup"><span data-stu-id="77a0b-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="77a0b-109">Volitelné rozhraní oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md)</span><span class="sxs-lookup"><span data-stu-id="77a0b-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="77a0b-110">Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.</span><span class="sxs-lookup"><span data-stu-id="77a0b-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="77a0b-111">Přijímá ID souboru nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="77a0b-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="77a0b-112">Přijímá rozhraní [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="77a0b-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="77a0b-113">Hodnota NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="77a0b-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="77a0b-114">Přijímá nalezené soubory nebo obory, které byly importovány.</span><span class="sxs-lookup"><span data-stu-id="77a0b-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77a0b-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="77a0b-115">Return Value</span></span>  
 <span data-ttu-id="77a0b-116">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="77a0b-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a0b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77a0b-117">Requirements</span></span>  
 <span data-ttu-id="77a0b-118">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="77a0b-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a0b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77a0b-119">See also</span></span>

- [<span data-ttu-id="77a0b-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77a0b-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="77a0b-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77a0b-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="77a0b-122">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="77a0b-122">ALink API</span></span>](index.md)
