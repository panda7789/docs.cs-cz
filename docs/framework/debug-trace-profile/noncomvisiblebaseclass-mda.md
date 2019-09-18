---
title: nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4340dd75e24ddeb01428159d5532b86e76fd8b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052441"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
Pomocník spravovaného ladění (MDA) je aktivován `QueryInterface` při volání z nativního nebo nespravovaného kódu na obálku s podporou modelu COM, která je odvozena ze základní třídy, která není viditelná v modelu COM. `nonComVisibleBaseClass`  Volání způsobí, že se třída MDA aktivuje pouze v případech, kdy volání vyžaduje rozhraní třídy `IDispatch` nebo výchozí spravovanou třídu viditelnou z modelu COM. `QueryInterface`  MDA se neaktivuje, pokud `QueryInterface` je pro explicitní rozhraní, které <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> má atribut použit a je explicitně implementováno třídou, která je viditelná v modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Bylo `QueryInterface` provedeno volání z nativního kódu, které se nedaří s COR_E_INVALIDOPERATION HRESULT.  Hodnota HRESULT může být způsobena nepovolenými `QueryInterface` voláními modulu runtime, která by způsobila aktivaci této aplikace MDA.  
  
## <a name="cause"></a>příčina  
 Modul runtime nemůže umožňovat `QueryInterface` volání rozhraní třídy nebo výchozího `IDispatch` rozhraní třídy viditelné v modelu COM, která je odvozena od třídy, která není viditelná jako model COM, z důvodu potenciálních problémů se správou verzí.  Například pokud byly některé veřejné členy přidány do základní třídy, která není viditelná v modelu COM, existující klienti modelu COM používající odvozenou třídu mohou potenciálně poškodit, protože tabulka odvozené třídy, která obsahuje členy základní třídy, by mohla být změněna tímto mění.  Explicitní rozhraní vystavená modelu COM nemají tento problém, protože neobsahují základní členy rozhraní v tabulce vtable.  
  
## <a name="resolution"></a>Řešení  
 Nezveřejňujte rozhraní třídy. Definujte explicitní rozhraní a použijte <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> k němu atribut.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Následuje příklad zprávy pro `QueryInterface` volání ve třídě `Derived` viditelné pomocí modelu COM, která je odvozena od třídy `Base`, která není viditelná z modelu COM.  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
