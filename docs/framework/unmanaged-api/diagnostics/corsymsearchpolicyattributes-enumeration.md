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
ms.openlocfilehash: 8af71314cf8a24c710d3b8980c082daaf9186715
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501869"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="1a9b4-102">CorSymSearchPolicyAttributes – výčet</span><span class="sxs-lookup"><span data-stu-id="1a9b4-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="1a9b4-103">Určuje zásadu, která se má použít při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="1a9b4-104">Tyto konstanty jsou používány metodami [ISymUnmanagedBinder2 –:: GetReaderForFile2 –](isymunmanagedbinder2-getreaderforfile2-method.md) a [Isymunmanagedbinder3 –:: GetReaderFromCallback –](isymunmanagedbinder3-getreaderfromcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a9b4-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a9b4-105">Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9b4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a9b4-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="1a9b4-107">Členové</span><span class="sxs-lookup"><span data-stu-id="1a9b4-107">Members</span></span>  
  
|<span data-ttu-id="1a9b4-108">Člen</span><span class="sxs-lookup"><span data-stu-id="1a9b4-108">Member</span></span>|<span data-ttu-id="1a9b4-109">Description</span><span class="sxs-lookup"><span data-stu-id="1a9b4-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="1a9b4-110">Vyhledá v registru cesty pro hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="1a9b4-111">Přistupuje k serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="1a9b4-112">Vyhledá cestu zadanou v adresáři ladění.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="1a9b4-113">Vyhledá PDB na místě, kde se nachází soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="1a9b4-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a9b4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a9b4-114">Requirements</span></span>  
 <span data-ttu-id="1a9b4-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1a9b4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9b4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a9b4-116">See also</span></span>

- [<span data-ttu-id="1a9b4-117">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1a9b4-117">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
