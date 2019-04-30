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
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933806"
---
# <a name="security-and-race-conditions"></a>Zabezpečení a konflikty časování
Další oblastí zájmu je potenciální bezpečnostní rizika zneužité časování. Existuje několik způsobů, ve kterých k tomu může dojít. Související témata, které následují popisují některé z hlavních problémů, které musí vývojáři vyhnout.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Časování v metody Dispose  
 Případě, že třída **Dispose** – metoda (Další informace najdete v tématu [uvolňování](../../../docs/standard/garbage-collection/index.md)) není synchronizována, je možné tento kód pro vyčištění uvnitř **Dispose** můžete spustit více než jednou, jak je znázorněno v následujícím příkladu.  
  
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
  
 Protože toto **Dispose** implementace není synchronizovaný, je možné, `Cleanup` má být volána nejprve jedno vlákno a pak druhého podprocesu před `_myObj` je nastavena na **null**. Zda se jedná o problém zabezpečení závisí na co se stane, když `Cleanup` spuštěn kód. Hlavní problém s nesynchronizované **Dispose** implementací zahrnuje použití popisovače prostředku, jako jsou například soubory. Nesprávné odstranění může způsobit nesprávné popisovač, kterou chcete použít, což často vede k ohrožení zabezpečení.  
  
## <a name="race-conditions-in-constructors"></a>Časování v konstruktorech  
 V některých aplikacích je možné pro ostatní vlákna pro přístup ke členům třídy před jejich konstruktor třídy zcela spustili. Měli byste zkontrolovat všechny třídy konstruktory, abyste měli jistotu, že pokud k tomu musí dojít, nebo synchronizaci vláken, v případě potřeby neexistují žádné problémy se zabezpečením.  
  
## <a name="race-conditions-with-cached-objects"></a>Ke konfliktům časování s objekty uložené v mezipaměti  
 Kód, který ukládá informace o zabezpečení nebo který používá zabezpečení přístupu kódu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operace může být také snadno napadnutelný časování Pokud jiné části třídy nejsou synchronizované odpovídajícím způsobem, jak je znázorněno v následujícím příkladu.  
  
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
  
 Pokud existují další cesty k `DoOtherWork` , který lze volat z jiného vlákna se stejným objektem, nedůvěryhodné volající může zpozdit poslední požadavek.  
  
 Pokud váš kód mezipaměti informace o zabezpečení, ujistěte se, abyste si pro toto ohrožení zabezpečení.  
  
## <a name="race-conditions-in-finalizers"></a>Časování v finalizační metody  
 V objektu, který odkazuje na statickou nebo nespravovaný prostředek, který poté uvolní v jeho finalizační metoda může také dojít ke konfliktům časování. Pokud více objektů sdílí prostředek, který je zpracováván v finalizační metodu třídy, musíte synchronizovat objekty veškerý přístup k prostředku.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
