---
title: Zabezpečení a konflikty časování
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
ms.openlocfilehash: 8980122acdd069bc840aa09129483a1cb9a379fd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705870"
---
# <a name="security-and-race-conditions"></a>Zabezpečení a konflikty časování
Další oblastí obav je potenciál bezpečnostních děr vycházejících ze sporných podmínek. Existuje několik způsobů, jak se k tomu může dojít. Dílčí témata, která následují, popisují některé hlavní nástrah, se kterými se vývojář musí vyhnout.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Konflikty časování v metodě Dispose  
 Pokud metoda **Dispose** třídy (pro další informace, viz [uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné, že čistící kód uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.  
  
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
  
 Vzhledem k tomu, že tato implementace **Dispose** není synchronizována, je možné, že `Cleanup` být volána prvním jedním vláknem a druhým vláknem, před `_myObj` je nastavena na **hodnotu null**. Bez ohledu na to, zda se jedná o zabezpečení, závisí na tom, co se stane, když `Cleanup` kód spouští. Hlavní problém s nesynchronizovanými implementacemi **Dispose** zahrnuje použití popisovačů prostředků, jako jsou soubory. Nesprávné vyřazení může způsobit použití chybného popisovače, což často vede k ohrožení zabezpečení.  
  
## <a name="race-conditions-in-constructors"></a>Konflikty časování v konstruktorech  
 V některých aplikacích může být možné, aby další vlákna mohla přistupovat ke členům třídy před tím, než se jejich konstruktory tříd úplně spustí. Měli byste zkontrolovat všechny konstruktory třídy, aby se zajistilo, že nedochází k žádným problémům se zabezpečením, pokud by k tomu došlo, nebo v případě potřeby synchronizaci vláken.  
  
## <a name="race-conditions-with-cached-objects"></a>Konflikty časování s objekty uloženými v mezipaměti  
 Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá operaci [vyhodnocení](../../../docs/framework/misc/using-the-assert-method.md) zabezpečení přístupu kódu, může být také ohrožen konflikty časování, pokud jiné části třídy nejsou vhodně synchronizovány, jak je znázorněno v následujícím příkladu.  
  
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
  
 Pokud existují další cesty `DoOtherWork`, které je možné volat z jiného vlákna se stejným objektem, může nedůvěryhodný volající nakládat za poptávkou.  
  
 Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, že je pro tuto chybu zabezpečení revidován.  
  
## <a name="race-conditions-in-finalizers"></a>Konflikty časování v finalizačních podmínkách  
 Ke konfliktům časování může dojít také v objektu, který odkazuje na statický nebo nespravovaný prostředek, který je poté uvolněn v jeho finalizační metodě. Pokud více objektů sdílí prostředek, který je manipulován v finalizační metodě třídy, musí objekty synchronizovat veškerý přístup k tomuto prostředku.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
