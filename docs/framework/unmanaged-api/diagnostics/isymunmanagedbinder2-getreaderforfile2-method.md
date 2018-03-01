---
title: "ISymUnmanagedBinder2::GetReaderForFile2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 270a154c40b85ad4774bececf12685393f4d6c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="c0373-102">ISymUnmanagedBinder2::GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c0373-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="c0373-103">Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní, které budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c0373-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="c0373-104">Tato metoda poskytuje rozšířené hledání pro soubor databáze (PDB) program, než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c0373-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0373-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0373-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0373-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0373-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="c0373-107">[v] Ukazatel rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="c0373-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="c0373-108">[v] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="c0373-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="c0373-109">[v] Ukazatel na cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c0373-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="c0373-110">[v] Hodnota [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady, který se má použít při vyhledávání pro čtečku symbol.</span><span class="sxs-lookup"><span data-stu-id="c0373-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c0373-111">[out] Ukazatele, který je nastavený s vráceným <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c0373-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0373-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0373-112">Return Value</span></span>  
 <span data-ttu-id="c0373-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c0373-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0373-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0373-114">Requirements</span></span>  
 <span data-ttu-id="c0373-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0373-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0373-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0373-116">Remarks</span></span>  
 <span data-ttu-id="c0373-117">Tato verze metody můžete vyhledat soubor PDB v oblastech než vpravo vedle modulu.</span><span class="sxs-lookup"><span data-stu-id="c0373-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="c0373-118">Zásady vyhledávání lze řídit tím, že zkombinujete [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c0373-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="c0373-119">Například `AllowReferencePathAccess | AllowSymbolServerAccess` hledá PDB vedle spustitelný soubor a na serveru symbol, ale není v registru nebo použijte cestu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="c0373-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="c0373-120">Pokud `searchPath` je zadán parametr, budou se vyhledávat vždy těchto adresářů.</span><span class="sxs-lookup"><span data-stu-id="c0373-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0373-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0373-121">See Also</span></span>  
 [<span data-ttu-id="c0373-122">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0373-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="c0373-123">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="c0373-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
