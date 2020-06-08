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
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes – výčet
Určuje zásadu, která se má použít při hledání čtečky symbolů. Tyto konstanty jsou používány metodami [ISymUnmanagedBinder2 –:: GetReaderForFile2 –](isymunmanagedbinder2-getreaderforfile2-method.md) a [Isymunmanagedbinder3 –:: GetReaderFromCallback –](isymunmanagedbinder3-getreaderfromcallback-method.md) .  
  
> [!IMPORTANT]
> Je bezpečnostním rizikem k otevření souboru programu databáze (PDB) z nedůvěryhodného zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`AllowRegistryAccess`|Vyhledá v registru cesty pro hledání symbolů.|  
|`AllowSymbolServerAccess`|Přistupuje k serveru symbolů.|  
|`AllowOriginalPathAccess`|Vyhledá cestu zadanou v adresáři ladění.|  
|`AllowReferencePathAccess`|Vyhledá PDB na místě, kde se nachází soubor. exe.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Výčty úložiště symbolů diagnostiky](diagnostics-symbol-store-enumerations.md)
