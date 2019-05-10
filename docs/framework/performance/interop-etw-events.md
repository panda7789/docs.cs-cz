---
title: Události Trasování událostí pro Windows interoperability
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38db390b8fad9cd36dacf33f9647b0272eddc4a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616413"
---
# <a name="interop-etw-events"></a>Události Trasování událostí pro Windows interoperability
<a name="top"></a> Události interoperability zaznamenat informace o Microsoft intermediate language (MSIL) zástupné procedury generování a ukládání do mezipaměti.  
  
 Tato kategorie se skládá z následujících událostí:  
  
- [ILStubGenerated události](#ilstubgenerated_event)  
  
- [ILStubCacheHit Event](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|Byl vytvořen testovací kód jazyka MSIL.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|win:UInt16|Identifikátor modulu.|  
|StubMethodID|win:UInt64|Metoda identifikátor zástupné procedury.|  
|StubFlags|win:UInt64|Příznaky pro zástupná procedura:<br /><br /> 0x1 – reverzní zprostředkovatele komunikace s objekty.<br /><br /> 0x2 - komunikace s objekty COM.<br /><br /> 0x4 - zástupné proceduře vygenerované pomocí NGen.exe.<br /><br /> 0x8 - delegáta.<br /><br /> 0x10 - arrgument proměnné.<br /><br /> 0x20 – nespravované volaný.|  
|ManagedInteropMethodToken|win:UInt32|Token pro spravované vzájemné spolupráce metody.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Obor názvů spravovaná metoda spolupráce.|  
|ManagedInteropMethodName|win:UnicodeString|Název spravované vzájemné spolupráce metody.|  
|ManagedInteropMethodSignature|win:UnicodeString|Podpis spravované vzájemné spolupráce metody.|  
|NativeMethodSignature|win:UnicodeString|Nativní metoda podpis.|  
|StubMethodSignature|win:UnicodeString|Podpis metody zástupných procedur.|  
|StubMethodILCode|win:UnicodeString|Kód jazyka MSIL pro metody zástupných procedur.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|Jazyk MSIL mezipaměti byl otevřen.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|win:UInt16|Identifikátor modulu.|  
|StubMethodID|win:UInt64|Metoda identifikátor zástupné procedury.|  
|ManagedInteropMethodToken|win:UInt32|Token pro spravované vzájemné spolupráce metody.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Obor názvů spravovaná metoda spolupráce.|  
|ManagedInteropMethodName|win:UnicodeString|Název spravované vzájemné spolupráce metody.|  
|ManagedInteropMethodSignature|win:UnicodeString|Podpis spravované vzájemné spolupráce metody.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
