---
title: CorSymSearchPolicyAttributes – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178352"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="b2249-102">CorSymSearchPolicyAttributes – výčet</span><span class="sxs-lookup"><span data-stu-id="b2249-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="b2249-103">Určuje zásadu, která má být použita při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="b2249-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="b2249-104">Tyto konstanty jsou používány metodami [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) a [ISymUnmanagedBinder3::GetReaderFromCallback.](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)</span><span class="sxs-lookup"><span data-stu-id="b2249-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2249-105">Je bezpečnostní riziko pro otevření souboru databáze programů (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="b2249-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2249-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2249-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="b2249-107">Členové</span><span class="sxs-lookup"><span data-stu-id="b2249-107">Members</span></span>  
  
|<span data-ttu-id="b2249-108">Člen</span><span class="sxs-lookup"><span data-stu-id="b2249-108">Member</span></span>|<span data-ttu-id="b2249-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b2249-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="b2249-110">Dotazuje registr na cesty pro vyhledávání symbolů.</span><span class="sxs-lookup"><span data-stu-id="b2249-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="b2249-111">Přistupuje k serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="b2249-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="b2249-112">Prohledá cestu zadanou v adresáři Ladění.</span><span class="sxs-lookup"><span data-stu-id="b2249-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="b2249-113">Vyhledá pdb v místě, kde je soubor EXE.</span><span class="sxs-lookup"><span data-stu-id="b2249-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2249-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2249-114">Requirements</span></span>  
 <span data-ttu-id="b2249-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b2249-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2249-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2249-116">See also</span></span>

- [<span data-ttu-id="b2249-117">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b2249-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
