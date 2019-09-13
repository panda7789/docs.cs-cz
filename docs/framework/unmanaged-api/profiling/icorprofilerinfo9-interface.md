---
title: ICorProfilerInfo9 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: af6bd02c6d4e88c72dca20d2520d1ecc8cf1c421
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928789"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 – rozhraní

Podtřída [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) , která poskytuje metody pro dotazování na informace o funkcích s více nativními verzemi kódu.  

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje. |
|[Metoda GetILToNativeMapping3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| Vzhledem k počáteční adrese nativního kódu vrací nativní informace mapování IL pro tuto verzi zpracovaných kompilátorem JIT kódu. |
|[Metoda GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód. |

## <a name="requirements"></a>Požadavky  
**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Hlaviček** CorProf.idl, CorProf.h  
**Verze rozhraní .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
