---
title: Zabezpečení a konflikty časování
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186783"
---
# <a name="security-and-race-conditions"></a>Zabezpečení a konflikty časování
Další oblastí zájmu je potenciál pro bezpečnostní díry využívané rasovými podmínkami. Existuje několik způsobů, jak k tomu může dojít. Dílčí témata, které následují, popisují některé z hlavních úskalí, kterým se vývojář musí vyhnout.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Sporné podmínky v metodě dispose  
 Pokud metoda **Dispose** třídy (další informace naleznete v [tématu Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) ) není synchronizována, je možné, že vyčištění kódu uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Vzhledem k **tomu, že** tato implementace `Cleanup` Dispose není synchronizována, je možné `_myObj` volat první vlákno a potom druhé vlákno před je nastavena na **hodnotu null**. Zda se jedná o problém zabezpečení `Cleanup` závisí na tom, co se stane při spuštění kódu. Hlavní problém s nesynchronizované **dispose** implementace zahrnuje použití popisovače prostředků, jako jsou soubory. Nesprávné vyřazení může způsobit použití nesprávného popisovače, což často vede k ohrožení zabezpečení.  
  
## <a name="race-conditions-in-constructors"></a>Závodní podmínky v konstruktorech  
 V některých aplikacích může být možné pro jiné podprocesy pro přístup členů třídy před jejich konstruktory třídy mají zcela spustit. Měli byste zkontrolovat všechny konstruktory třídy a ujistěte se, že neexistují žádné problémy se zabezpečením, pokud k tomu dojde, nebo v případě potřeby synchronizovat vlákna.  
  
## <a name="race-conditions-with-cached-objects"></a>Podmínky časovoleb s objekty uloženými v mezipaměti  
 Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [Assert](../../../docs/framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také zranitelný vůči časovacím podmínkám, pokud ostatní části třídy nejsou odpovídajícím způsobem synchronizovány, jak je znázorněno v následujícím příkladu.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 Pokud existují jiné cesty, `DoOtherWork` které mohou být volány z jiného vlákna se stejným objektem, nedůvěryhodný volající může proklouznout kolem poptávky.  
  
 Pokud váš kód ukládá informace o zabezpečení do mezipaměti, zkontrolujte, zda se jedná o tuto chybu zabezpečení.  
  
## <a name="race-conditions-in-finalizers"></a>Podmínky závodu ve finalizačních metodách  
 Časování podmínky může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který pak uvolní ve své finalizační metodě. Pokud více objektů sdílet prostředek, který je manipulováno ve finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
