---
title: Události Trasování událostí pro Windows interoperability
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db68cdce0db4f8f4d85e9d1dd03720bf235d865
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974923"
---
# <a name="interop-etw-events"></a>Události Trasování událostí pro Windows interoperability
Události vzájemné spolupráce zachytí informace o generování a ukládání procedury do mezipaměti v jazyce MSIL (Microsoft Intermediate Language).  

## <a name="ilstubgenerated-event"></a>Událost ILStubGenerated

Klíčové slovo a úroveň jsou uvedeny v následující tabulce. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Obsah|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|Byl vygenerován zástupný kód jazyka MSIL.|  
  
 V následující tabulce jsou uvedena data události.  
  
|název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ModuleID|Win: UInt16|Identifikátor modulu.|  
|StubMethodID|Win: UInt64|Identifikátor metody zástupné procedury.|  
|StubFlags|Win: UInt64|Příznaky pro zástupnou proceduru:<br /><br /> 0x1 – reverzní interoperabilita<br /><br /> pře0x2-COM Interop.<br /><br /> 0x4 – zástupné procedury generované NGen. exe.<br /><br /> 0x8 – Delegate<br /><br /> Argument 0x10-Variable<br /><br /> 0x20 – nespravovaný volaný|  
|ManagedInteropMethodToken|Win: UInt32|Token pro spravovanou metodu spolupráce|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Obor názvů spravované metody spolupráce.|  
|ManagedInteropMethodName|Win: UnicodeString|Název spravované metody spolupráce.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Podpis spravované metody spolupráce.|  
|NativeMethodSignature|Win: UnicodeString|Signatura nativní metody.|  
|StubMethodSignature|Win: UnicodeString|Podpis metody zástupné procedury|  
|StubMethodILCode|Win: UnicodeString|Kód jazyka MSIL pro metodu zástupné procedury.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="ilstubcachehit-event"></a>Událost ILStubCacheHit  

Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Obsah|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|K mezipaměti MSIL bylo přistup.|  
  
 V následující tabulce jsou uvedena data události.  
  
|název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ModuleID|Win: UInt16|Identifikátor modulu.|  
|StubMethodID|Win: UInt64|Identifikátor metody zástupné procedury.|  
|ManagedInteropMethodToken|Win: UInt32|Token pro spravovanou metodu spolupráce|  
|ManagedInteropMethodNameSpace|Win: UnicodeString|Obor názvů spravované metody spolupráce.|  
|ManagedInteropMethodName|Win: UnicodeString|Název spravované metody spolupráce.|  
|ManagedInteropMethodSignature|Win: UnicodeString|Podpis spravované metody spolupráce.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
