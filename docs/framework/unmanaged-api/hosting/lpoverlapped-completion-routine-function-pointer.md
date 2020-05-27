---
title: LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: c0bdd9e59f5794dbb0d447dc2cc6cb682bfdf09f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008479"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci
Odkazuje na funkci, která upozorňuje hostitele, když je dokončeno překrytí (tj. asynchronní) vstupně-výstupní operace se zařízením.  
  
 Tento ukazatel funkce je zastaralý v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 pro Hodnota, která je kód chyby v případě, že zařízení bylo zavřeno; v opačném případě je tato hodnota nulová.  
  
 Když se zařízení uzavírá, způsobí to okamžité dokončení všech nedokončených vstupně-výstupních operací.  
  
 `dwNumberOfBytesTransfered`  
 pro Počet bajtů přenesených operací I/O.  
  
 `lpOverlapped`  
 pro Ukazatel na strukturu, která obsahuje informace, které se mají použít k dokončení vstupně-výstupních požadavků.  
  
## <a name="remarks"></a>Poznámky  
 Funkce, na které `LPOVERLAPPED_COMPLETION_ROUTINE` jsou body funkce zpětného volání a které musí být implementovány zapisovačí hostující aplikace. Funkce zpětného volání umožňuje hostiteli zpracovat dokončenou vstupně-výstupní žádost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Knihovny Mscorwks. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
