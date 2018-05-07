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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-race-conditions"></a>Zabezpečení a konflikty časování
Další oblastí zájmu je potenciální bezpečnostní rizika zneužité časování. Existuje několik způsobů, ve kterých k tomu může dojít. Související témata, které následují popisují některé z hlavních problémů, kterým musí vývojář vyhnout.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Konflikty časování v metodu Dispose  
 Pokud na třídu **Dispose** – metoda (Další informace najdete v tématu [uvolňování paměti](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné tento kód čištění uvnitř **Dispose** lze spustit více než jednou, jak je znázorněno v následujícím příkladu.  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Protože to **Dispose** implementace není synchronizována, je možné pro `Cleanup` má být volána nejprve jedno vlákno a pak druhý vlákno před `_myObj` je nastaven na **null**. Jestli se jedná o problém zabezpečení závisí na co se stane, když `Cleanup` kód běží. Hlavní problém s nesynchronizovaných **Dispose** implementací zahrnuje použití popisovače prostředku, jako jsou například soubory. Nesprávné odstranění může způsobit nesprávnou popisovač použije, což často vede k ohrožení zabezpečení.  
  
## <a name="race-conditions-in-constructors"></a>Konflikty časování v konstruktorech  
 V některých aplikacích může být jiná vlákna přístup ke členům třídy před jejich konstruktory třídy zcela spustí. Měli byste zkontrolovat všechny třídy konstruktory a ujistěte se, že pokud tomu má dojít, nebo synchronizovat vláken v případě potřeby neexistují žádné problémy se zabezpečením.  
  
## <a name="race-conditions-with-cached-objects"></a>Konflikty časování s objekty v mezipaměti  
 Kód, který ukládá do mezipaměti informace o zabezpečení nebo používá zabezpečení přístupu kódu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operace může být ohrožen časování Pokud dalších částí třídy nejsou správně synchronizovány, jak je znázorněno v následujícím příkladu.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 Pokud jsou jiné cesty k `DoOtherWork` , lze volat z jiného vlákna se stejný objekt, nedůvěryhodný volající může proklouznout požadavku.  
  
 Pokud váš kód ukládá do mezipaměti informace o zabezpečení, ujistěte se, zkontrolujte pro toto ohrožení zabezpečení.  
  
## <a name="race-conditions-in-finalizers"></a>Konflikty časování v finalizační metody  
 Konflikty časování může dojít také v objektu, který odkazuje na statickou nebo nespravovaný prostředek, který poté uvolní v jeho finalizační metodu. Pokud více objektů sdílet na prostředek, který je v finalizační metodu třídy a s nimi manipulovat, musí synchronizovat objekty veškerý přístup k prostředku.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
