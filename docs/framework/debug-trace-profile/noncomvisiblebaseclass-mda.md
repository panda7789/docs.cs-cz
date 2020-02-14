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
ms.openlocfilehash: b46d5c6ffbf12efbae113a95bbfccd5742ec9ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217303"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
V případě, že je volání `QueryInterface` provedeno pomocí nativního nebo nespravovaného kódu na obálku s podporou modelu COM, která je odvozena ze základní třídy, která není viditelná v modelu COM, je aktivována aplikace `nonComVisibleBaseClass` Managed Debugging Assistant (MDA).  `QueryInterface` volání způsobí, že se třída MDA aktivuje pouze v případech, kdy volání vyžádá rozhraní třídy nebo výchozí `IDispatch` spravované třídy viditelné v modelu COM.  MDA není aktivován, je-li `QueryInterface` pro explicitní rozhraní, které má atribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použit a je explicitně implementováno třídou, která je viditelná pro modul COM.  
  
## <a name="symptoms"></a>Příznaky  
 `QueryInterface` volání z nativního kódu, který selhává s COR_E_INVALIDOPERATION HRESULT.  Hodnota HRESULT může být způsobena tím, že modul runtime nepovoluje `QueryInterface` volání, která by způsobila aktivaci tohoto MDA.  
  
## <a name="cause"></a>Příčina  
 Modul runtime nemůže umožňovat `QueryInterface` volání rozhraní třídy nebo výchozího `IDispatch` rozhraní třídy viditelné v modelu COM, které je odvozeno od třídy, která není viditelná jako model COM, z důvodu potenciálních problémů se správou verzí.  Například pokud byly některé veřejné členy přidány do základní třídy, která není viditelná v modelu COM, existující klienti modelu COM používající odvozenou třídu mohou potenciálně poškodit, protože tabulka odvozené třídy, která obsahuje členy základní třídy, by mohla být změněna tímto mění.  Explicitní rozhraní vystavená modelu COM nemají tento problém, protože neobsahují základní členy rozhraní v tabulce vtable.  
  
## <a name="resolution"></a>Řešení  
 Nezveřejňujte rozhraní třídy. Definujte explicitní rozhraní a použijte pro něj atribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Následuje příklad zprávy pro `QueryInterface` volání `Derived` třídy viditelné v modelu COM, které jsou odvozeny z `Base`třídy, která není viditelná pro model COM.  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
