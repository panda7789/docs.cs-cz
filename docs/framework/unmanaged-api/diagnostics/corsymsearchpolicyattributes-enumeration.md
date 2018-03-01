---
title: "CorSymSearchPolicyAttributes – výčet"
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
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc1bef8c393a7778c194b2d4d45c3abdb583fecf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="9aae1-102">CorSymSearchPolicyAttributes – výčet</span><span class="sxs-lookup"><span data-stu-id="9aae1-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="9aae1-103">Určuje zásady, který se má použít při vyhledávání pro čtečku symbol.</span><span class="sxs-lookup"><span data-stu-id="9aae1-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="9aae1-104">Tyto konstanty jsou používány [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [isymunmanagedbinder3::getreaderfromcallback –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9aae1-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9aae1-105">Je bezpečnostní riziko pro otevření souboru databáze (PDB) program z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="9aae1-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aae1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aae1-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="9aae1-107">Členové</span><span class="sxs-lookup"><span data-stu-id="9aae1-107">Members</span></span>  
  
|<span data-ttu-id="9aae1-108">Člen</span><span class="sxs-lookup"><span data-stu-id="9aae1-108">Member</span></span>|<span data-ttu-id="9aae1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9aae1-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="9aae1-110">Vyhledá v registru cesty pro hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="9aae1-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="9aae1-111">Přístup k serveru symbol.</span><span class="sxs-lookup"><span data-stu-id="9aae1-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="9aae1-112">Najde v adresáři ladění zadanou cestu.</span><span class="sxs-lookup"><span data-stu-id="9aae1-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="9aae1-113">Vyhledá PDB na místě, kde je soubor .exe.</span><span class="sxs-lookup"><span data-stu-id="9aae1-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9aae1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9aae1-114">Requirements</span></span>  
 <span data-ttu-id="9aae1-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9aae1-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aae1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aae1-116">See Also</span></span>  
 [<span data-ttu-id="9aae1-117">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="9aae1-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
