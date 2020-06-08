---
title: ISymUnmanagedWriter4 – rozhraní
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 21d6520aae1367368973da1692f6bca3aeb2c129
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493653"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 – rozhraní
Rozhraní Isymunmanagedwriter4 –  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetDebugInfoWithPadding – metoda](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Funguje stejně jako [Metoda GetDebugInfo –](isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněn nulami za ukončovacím znakem null, aby data řetězce měla pevnou velikost `MAX_PATH` . Odsazení je zadáno pouze v případě, že délka řetězce cesty je menší než `MAX_PATH` .<br /><br /> To usnadňuje psaní nástrojů, které rozdílují soubory PE.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 – rozhraní](isymunmanagedwriter3-interface.md)
