---
title: Zabezpečení a konflikty časování
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: a667bf69ba72cbe203bd2603c4c6b7a1e58a6d43
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555107"
---
# <a name="security-and-race-conditions"></a>Zabezpečení a konflikty časování

Další oblastí obav je potenciál bezpečnostních děr vycházejících ze sporných podmínek. Existuje několik způsobů, jak se k tomu může dojít. Dílčí témata, která následují, popisují některé hlavní nástrah, se kterými se vývojář musí vyhnout.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Konflikty časování v metodě Dispose  

Pokud metoda **Dispose** třídy (pro další informace, viz [uvolňování paměti](../garbage-collection/index.md)) není synchronizována, je možné, že čistící kód uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.  
  
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
  
Vzhledem k tomu, že tato implementace **Dispose** není synchronizována, je možné ji `Cleanup` volat prvním jedním vláknem a poté druhým vláknem, `_myObj` aby byla nastavena na **hodnotu null**. Bez ohledu na to, zda se jedná o zabezpečení, závisí na tom, co se stane při `Cleanup` spuštění kódu. Hlavní problém s nesynchronizovanými implementacemi **Dispose** zahrnuje použití popisovačů prostředků, jako jsou soubory. Nesprávné vyřazení může způsobit použití chybného popisovače, což často vede k ohrožení zabezpečení.  
  
## <a name="race-conditions-in-constructors"></a>Konflikty časování v konstruktorech

V některých aplikacích může být možné, aby další vlákna mohla přistupovat ke členům třídy před tím, než se jejich konstruktory tříd úplně spustí. Měli byste zkontrolovat všechny konstruktory třídy, aby se zajistilo, že nedochází k žádným problémům se zabezpečením, pokud by k tomu došlo, nebo v případě potřeby synchronizaci vláken.  
  
## <a name="race-conditions-with-cached-objects"></a>Konflikty časování s objekty uloženými v mezipaměti  

Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [vyhodnocení](../../framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také ohrožen konflikty časování, pokud jiné části třídy nejsou vhodně synchronizovány, jak je znázorněno v následujícím příkladu.  
  
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
  
Pokud existují další cesty `DoOtherWork` , které mohou být volány z jiného vlákna se stejným objektem, nedůvěryhodný volající může nakládat za poptávku.  
  
Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, že je pro tuto chybu zabezpečení revidován.  
  
## <a name="race-conditions-in-finalizers"></a>Konflikty časování v finalizačních podmínkách  

Ke konfliktům časování může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který je poté uvolněn v jeho finalizační metodě. Pokud více objektů sdílí prostředek, který je manipulován v finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](secure-coding-guidelines.md)
- [ASP.NET Core zabezpečení](/aspnet/core/security/)
